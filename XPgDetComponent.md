# XPgDetComponent
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
An abstract class used as a base for providing details page parameters. It holds the <code>xpgDetailsPageConfig</code> object, which contains configuration settings and callbacks for the detail page.
### XPgDetailsParam
- A concrete class extending <code>XPgDetailsParamProvider</code>. It provides a specific implementation of the <code>XPgDetailsParamProvider</code> service, initialized with <code>xpgDetailsPageConfig</code>. This class is used to pass configuration details to the component.
 ### XpgDetailsPageConfig
-  An interface defining the structure and properties required for configuring the details page. This interface is used to set up the detail page and control its behavior within the <code>XPgDetComponent</code>.
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

![image](https://github.com/user-attachments/assets/b92e7c1c-9336-476b-8ebe-11a2800d6a87)

 
