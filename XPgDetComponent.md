# XPgDetComponent
This component typically handles displaying fields, handling user inputs, and managing the layout for a detailed page view. It is part of a dynamic page generation system, where it renders detailed information based on the provided configuration and parameters.
## Code Example

```typescript
this.component = XPgDetComponent;
this.injector = Injector.create({
  providers: [
    {
      provide: XPgDetailsParamProvider,
      useValue: new XPgDetailsParam(xpgDetailsPageConfig),
    },
  ],
  parent: this.inj,
});
```
### Component Assignment:

- The component <code>XPgDetComponent</code> is assigned to the component property.
### Injector Creation:

- Create a new Injector using  <code>Injector.create()</code>.
- The providers array contains a provider for  <code>XPgDetailsParamProvider</code>, which uses the value of a new XPgDetailsParam initialized with  <code>xpgDetailsPageConfig</code>.
### Parent Injector:

- The parent injector is set to  <code>this.inj</code>, which indicates the parent context for dependency resolution.

### XPgDetailsParamProvider
- <code>XPgDetailsParamProvider</code> serves as a dependency injection , enabling the injection of a configuration object or parameters (e.g., an instance of XPgDetailsParam) required to render or control the behavior of a detailed page component.
### XPgDetailsParam
- <code>XPgDetailsParam</code> is a configuration class used to pass parameters and settings for rendering or managing detailed pages in an application. It typically contains properties like layout, field definitions, or data bindings to dynamically configure the detail view.
 ### XpgDetailsPageConfig
-  <code>xpgDetailsPageConfig</code> is an object that holds the configuration settings for a detail page, such as layout, fields, data, and behavior, enabling dynamic rendering and customization of the page..
### XPgDetPageConfig Properties

| **Property**          | **Type**                             | **Function**                                                                                     |
|------------------------|--------------------------------------|-------------------------------------------------------------------------------------------------|
| `PageState`           | `Enum`                              | Represents different states of the page.                                                       |
| `pageState`           | `PageState`                         | Tracks the current state of the page, initialized to `Loading`.                                |
| `isProcessing`        | `boolean`                           | Indicates if a process is ongoing.                                                             |
| `isDisabled`          | `boolean`                           | Determines if the UI is disabled.                                                              |
| `isDataNotRequired`   | `boolean`                           | Indicates if data is not required.                                                             |
| `path`                | `string`                            | URL path associated with the page.                                                             |
| `entityName`          | `string`                            | Name of the entity for the page.                                                               |
| `appMenu`             | `AppMenuDto`                        | Represents application menu details.                                                           |
| `id`                  | `string`                            | Unique identifier for the current entity.                                                      |
| `item`                | `ItemEntityDto`                     | Represents the current entity data.                                                            |
| `initialItem`         | `ItemEntityDto`                     | Stores the initial data of the entity.                                                         |
| `defaultItem`         | `ItemEntityDto`                     | Stores the default values of the entity.                                                       |
| `pageTitle`           | `string \| null`                    | Title of the page.                                                                              |
| `pageSubTitle`        | `string \| null`                    | Subtitle of the page.                                                                           |
| `pageParams`          | `PageParams \| null`                | Parameters associated with the page.                                                           |
| `xpgDetailsPageConfig`| `XpgDetailsPageConfig`              | Configuration object for XPG Details.                                                          |
| `pageMode`            | `PageMode \| null`                  | Mode of the page (e.g., edit, read).                                                           |
| `orgPageMode`         | `PageMode \| null`                  | Stores the original page mode.                                                                 |
| `readMode`            | `boolean`                           | Indicates if the page is in read-only mode.                                                    |
| `formGroup`           | `FormGroup`                         | Reactive form group for managing form controls.                                                |
| `properties`          | `Property[]`                        | List of properties to display.                                                                 |
| `editProperties`      | `Property[]`                        | List of properties used for editing.                                                           |
| `layoutModels`        | `LayoutModel[]`                     | Layout configurations for the page.                                                            |
| `unique`              | `string[]`                          | Array of unique fields for validation.                                                         |
| `valueObjects`        | `{ fieldName: any }`                | Holds value objects for specified field names.                                                 |
| `cascadeProps`        | `{ fieldName: Property[] }`         | Represents cascading properties based on field names.                                          |
| `requiredIfProps`     | `{ [x: string]: RequiredIfProp[] }`  | Specifies properties required conditionally.                                                   |
| `objectItems`         | `ItemEntityDto`                     | Represents entity data for objects.                                                            |
| `attachment`          | `{ [x: string]: FilePathDto }`      | Stores a single file attachment.                                                               |
| `attachments`         | `{ [x: string]: FilePathDto[] }`    | Stores multiple file attachments.                                                              |
| `selectOptions`       | `{ [x: string]: LookUpProp }`       | Lookup options for dropdowns.                                                                  |
| `selectEmptyOptions`  | `any[]`                             | Placeholder for empty dropdown selections.                                                     |
| `destroy$`            | `Subject<void>`                     | Manages component lifecycle and unsubscribes from observables.                                 |
| `nameField`           | `string`                            | Represents the name field of the entity.                                                       |
| `codeField`           | `string`                            | Represents the code field of the entity.                                                       |
| `defaultPickerValue`  | `Date`                              | Default value for date picker components.                                                      |
| `shortcuts`           | `ShortcutInput[]`                   | List of keyboard shortcuts for the page.                                                       |
| `downloading`         | `boolean`                           | Indicates if a download process is ongoing.                                                    |
| `tabLoading`          | `boolean`                           | Tracks if the tab content is currently loading.                                                |
| `disablePrevTab`      | `boolean`                           | Disables the previous tab navigation.                                                          |
| `disableNextTab`      | `boolean`                           | Disables the next tab navigation.                                                              |
| `activetabIndex`      | `number`                            | Index of the currently active tab.                                                             |
| `activeTab`           | `any`                               | Represents the currently active tab.                                                           |
| `showPrevNext`        | `boolean`                           | Toggles visibility of previous and next navigation buttons.                                     |
| `showSaveStay`        | `boolean`                           | Toggles visibility of the "Save and Stay" button.                                              |
| `showSave`            | `boolean`                           | Toggles visibility of the "Save" button.                                                       |

---

## OutPut
### Overview
The  image shows a form for creating or editing an email template in the GeoStem application.

![image](https://github.com/user-attachments/assets/b92e7c1c-9336-476b-8ebe-11a2800d6a87)
- **BrokerRejectedMail**:Indicates the name of the template being created or edited
- **Code**: A unique identifier for the email template. This is often a system-generated value.
- **Template Type**:Specifies the format of the email content. In this case, it is an HTML-based email template.
- **Subject**: The subject line for the email, which can include default text or a placeholder for dynamic content.

 
