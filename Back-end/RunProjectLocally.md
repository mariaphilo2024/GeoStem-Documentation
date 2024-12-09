## Run the Project Locally   
                                                                                                                          
### Get Started - WebApi (ASP.NET Core)
Setup Your Development Environment
**Pre-Requirements**

https://visualstudio.microsoft.com/vs/

https://www.microsoft.com/net/download/dotnet-core/


Go to the aspnet-core folder, open GeoStem.sln

1. Create the Database
Connection String
Step 1. Right Click GeoStem.HttpApi.Host project and select Manage User Secrets

Step 2. This opens the secrets.json

Step 3. Replace the content as below:
{
  "App:CorsOrigins":         "https://*.GeoStem.com,http://localhost:4210,https://localhost:44307,http://localhost:54321",
  "App:AngularUrl": "http://localhost:4210",
  "App:SelfUrl": "https://localhost:44353",
  "AuthServer:Authority": "https://localhost:44353",
  "ConnectionStrings:Default": "Data Source=(localdb)\\mssqllocaldb;Initial Catalog=focali-db;Integrated Security=True;MultipleActiveResultSets=True",
  "MarineTraffic:ApiKey": "",
  "Storage:Azure": "DefaultEndpointsProtocol=https;AccountName=focalidev;AccountKey=PDOk3tmy9XvNEW55NdVXDt8YINp/S4ehYQ+4NHfZj5VDu710PxRtpspdSTcm+gvwB1qNTPWP3l3yxQpQ3bIcgA==;EndpointSuffix=core.windows.net",
  "StormGlass:ApiKey": "",
  "Twilio:AccoiuntSid": "",
  "Twilio:AuthToken": "",
  "Twilio:From": "",
  "APPLICATIONINSIGHTS_CONNECTION_STRING": "InstrumentationKey=a5bc0bed-6d2f-4c0f-9211-033685b157fe;IngestionEndpoint=https://centralindia-0.in.applicationinsights.azure.com/"
}

Repeat Step 1-3 for GeoStem.DbMigrator and GeoStem.EntityFrameworkCore.DbMigrations project with below content
{
  "ConnectionStrings:Default": "Data Source=(localdb)\\mssqllocaldb;Initial Catalog=focali-db;Integrated Security=True;MultipleActiveResultSets=True"
}

The solution is configured to use Entity Framework Core with MS SQL Server

Apply the Migrations
The solution uses the https://docs.microsoft.com/en-us/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli. So, you need to apply migrations to create the database.
The solution has AgencyPlatform.DbMigrator console application which applies migrations and seeds the initial data. It is useful for development as well as in the production environment.
You have already changed the connection string of GeoStem.DbMigrator as per the above steps.
Right click GeoStem.DbMigrator project and select Set as StartUp Project
Hit F5 (or Ctrl+F5) to run the application.
Initial seed data creates the admin user in the database (with the password is 1q2w3E*) which is then used to login to the application.

Development time update using EF Core Update-Database Command
Use the Ef Core Update-Database command which applies pending schema migrations during development time.
Right click to the GeoStem.HttpApi.Host project and select Set as StartUp Project:
Open the Package Manager Console, select GeoStem.EntityFrameworkCore project as the Default Project and run the Update-Database command:
GeoStem.DbMigrator tool, always migrates the schema and seeds the database, where Update-Database only migrates the schema.

Run the Application
Ensure that the GeoStem.HttpApi.Host project is the startup project and run the application which will open a Swagger UI in your browser.
      Use Ctrl+F5 in Visual Studio (instead of F5) to run the application without debugging. If you don't have a         debug purpose, this will be faster.
You can see the application APIs and test them here. Get https://swagger.io/tools/swagger-ui/ about the Swagger UI.

Authorization for the Swagger UI
        Most of the HTTP APIs require authentication & authorization. If you want to test authorized APIs, manually           go to login URL (https://localhost:**/Account/Login), enter admin as the username and 1q2w3E*             as the password to login to the application. Then you will be able to execute authorized APIs too.

Get Started UI - Angular (Web)
Setup Development Environment

Pre-Requirements
https://code.visualstudio.com/

https://nodejs.org/en/ & https://yarnpkg.com/getting-started/install/

https://cli.angular.io/

https://docs.abp.io/en/abp/3.3/CLI

https://docs.volta.sh/guide/getting-started


Run the Angular App
Open angular folder
Open the file AgencyPlatform.code-workspace in VS Code
Open a command line terminal
Enter the command yarn

Once all node modules are loaded, execute yarn start command
It may take a longer time for the first build. Once it finishes, it opens the Angular UI in your default browser with the http://localhost:4210/ address. Enter admin as the username and 1q2w3E* as the password to login to the application.

                                                                                                                                            Back To Main Page

