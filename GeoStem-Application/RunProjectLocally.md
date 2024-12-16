# GeoStem


##### Tech Stack
- [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)
- [Angular](https://angular.io)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [Flutter](https://flutter.dev/docs/development/tools/vs-code)

## Get Started - WebApi (ASP.NET Core)
#### Setup Your Development Environment
_Pre-Requirements_
* [Visual Studio 2022](https://visualstudio.microsoft.com/vs/)
* [.NET Core 7+](https://www.microsoft.com/net/download/dotnet-core/)

Go to the `aspnet-core` folder, open `GeoStem.sln`

### 1. Create the Database

##### Connection String

Step 1. Right Click `GeoStem.HttpApi.Host` project and select `Manage User Secrets`


Step 2. This opens the `secrets.json`

Step 3. Replace the content as below:
````json
{
  "App": {
    "SelfUrl": "https://localhost:44351",
    "ClientUrl": "http://localhost:4410",
    "CorsOrigins": "https://*.GeoStem.com,http://localhost:4410",
    "RedirectAllowedUrls": "http://localhost:4410"
  },
  "MyAppCertificate": {
    "X590": "agyge$56nunasopj"
  },
  "ConnectionStrings": {
    "Default": "Server=localhost\\SQLEXPRESS;Database=GeoStem;Trusted_Connection=True;TrustServerCertificate=True"
  },
  "AuthServer": {
    "Authority": "https://localhost:44351",
    "RequireHttpsMetadata": "false",
    "SwaggerClientId": "GeoStem_Swagger"
  },
  "StringEncryption": {
    "DefaultPassPhrase": "N2A9CNDxecVvXGaR"
  },
  "Storage:Azure": "DefaultEndpointsProtocol=https;AccountName=geostemuat;AccountKey=t/lYSw9x/o64os8tUwFl3GUXTfg1W//LEemv0qAdArVflCKPLiuxknZdhTPlJZeJrp0kBVj+w6qN+AStvyoAnw==;EndpointSuffix=core.windows.net",

  "AzureAd:TenantId": "b364406c-7174-462e-97cd-a4fbe7f1c9ee",
  "AzureAd:ClientId": "a7bc52e1-db90-4f19-b497-3dd5b43cc6c0",
  "AzureAd:ClientSecret": "Ss38Q~jjlf.21HiPRW680TKWzmCdy8IcytyKpdbx",
  "AzureAd:CallbackPath": "/signin-azuread-oidc"

  "AzureAd:TenantId": "b364406c-7174-462e-97cd-a4fbe7f1c9ee",
  "AzureAd:ClientId": "a7bc52e1-db90-4f19-b497-3dd5b43cc6c0",
  "AzureAd:ClientSecret": "w_n8Q~FjdNTvEEGWVvFoZ-0NVh0gIqBGEJw6tcXa",
  "AzureAd:CallbackPath": "/signin-azuread-oidc"
  "AzureAd:TenantId": "b364406c-7174-462e-97cd-a4fbe7f1c9ee",
  "AzureAd:ClientId": "a7bc52e1-db90-4f19-b497-3dd5b43cc6c0",
  "AzureAd:ClientSecret": "FD.8Q~edDQy3Vm~hJ1j1JdmE0mWtQ2OdZajOBa8v",
  "AzureAd:CallbackPath": "/signin-azuread-oidc"
}
````

![Alt text](docs/images/screenshot-user-secrets-002.png?raw=true "Manage User Secrets")

The solution is configured to use **Entity Framework Core** with **MS SQL Server**

##### Apply the Migrations

The solution uses the [Entity Framework Core Code First Migrations](https://docs.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli). So, you need to apply migrations to create the database.

The solution has `GeoStem.DbMigrator` console application which applies migrations and also **seeds the initial data**. It is useful on **development** as well as on **production** environment.

> You have already changed the connection string of `GeoStem.DbMigrator` as per above steps. 

- Right click `GeoStem.DbMigrator` project and select **Set as StartUp Project**
- Hit F5 (or Ctrl+F5) to run the application.

> Initial seed data creates the `admin` user in the database (with the password is `1q2w3E*`) which is then used to login to the application.

###### Development time update using EF Core Update-Database Command

Use the Ef Core `Update-Database` command which applies pending schema migrations during development time.

- Right click to the `AgencyPlatform.HttpApi.Host` project and select **Set as StartUp Project**: 
- Open the **Package Manager Console**, select `GeoStem.EntityFrameworkCore` project as the **Default Project** and run the `Update-Database` command:

> **`GeoStem.DbMigrator` tool**, always migrates the schema and seeds the database, where `Update-Database` only migrates the schema.

##### Run the Application
Ensure that the `GeoStem.HttpApi.Host` project is the startup project and run the application which will open a **Swagger UI** in your browser.

> Use Ctrl+F5 in Visual Studio (instead of F5) to run the application without debugging. If you don't have a debug purpose, this will be faster.

You can see the application APIs and test them here. Get [more info](https://swagger.io/tools/swagger-ui/) about the Swagger UI.

###### Authorization for the Swagger UI
> Most of the HTTP APIs require authentication & authorization. If you want to test authorized APIs, manually go to login url (`https://localhost:**/Account/Login`), enter `admin` as the username and `1q2w3E*` as the password to login to the application. Then you will be able to execute authorized APIs too.


## Get Started UI - Angular (Web)

#### Setup Your Development Environment
_Pre-Requirements_
* [Visual Studio Code](https://code.visualstudio.com/)
* [npm](https://nodejs.org/en/) & [yarn](https://yarnpkg.com/getting-started/install/)
* [Angular CLI](https://cli.angular.io/)
* [ABP CLI](https://docs.abp.io/en/abp/3.3/CLI)
* [Volta](https://docs.volta.sh/guide/getting-started)

#### Run the Angular App
- Open `angular` folder
- Open the file `GeoStem.code-workspace` in VS Code
- Open a command line terminal
- Enter the command `yarn`
- Once all node modules are loaded, execute `yarn start` command

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

> Enter `admin` as the username and `1q2w3E*` as the password to login to the application.

### Flutter (Mobile)

#### Setup Your Development Environment
_Pre-Requirements_
- [Install Flutter](https://docs.flutter.dev/get-started/install)
- [Install the VS Code Flutter and Dart plugins](https://flutter.dev/docs/get-started/editor?tab=vscode)

#### Run the Flutter App
- Open `flutter` folder
- Open the file `GeoStem.code-workspace` in VS Code
- Press `F5` to start
