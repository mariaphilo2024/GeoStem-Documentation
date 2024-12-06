# XPgDetailsComponent
The <code>XPgDetailsComponent</code> is a dynamic Angular component designed to display detailed information about a specific item or entity. It is highly configurable, leveraging injected parameters (e.g., <code>XPgDetailsParam)</code> to customize its behavior and content at runtime. This makes it reusable and adaptable for various use cases where detailed entity views are required.
## Code Example

```typescript
this.component = XPgDetailsComponent;
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
### Component Assignment
- The <code>XPgDetailsComponent</code> is assigned to the <code>this.component</code> property, preparing it for dynamic rendering.
 ### Injector Creation
An Injector is created using <code>Injector.create()</code>. The configuration includes:

- **Providers**: Specifies the services to inject.
- **XPgDetailsParamProvider**: A provider that uses <code>XPgDetailsParam</code> with the given <code>xpgDetailsPageConfig </code>as its value.
- **Parent Injector**: The parent key refers to <code>this.inj</code>, which serves as the parent injector for resolving additional dependencies.
- **XPgDetailsParam** is a configuration class used to pass parameters to the <code>XPgDetailsComponent</code>. It encapsulates the data and settings required to customize the component's behavior, such as layout, field mappings, or entity-specific details.
- **xpgDetailsPageConfig** is an instance of a configuration object (likely based on the <code>XPgDetailsParam</code> class) that defines the settings and data structure for rendering the <code>XPgDetailsComponent</code>.

  # Properties of xpgDetailsPageConfig:


| **Property**           | **Type**                          | **Function**                                                                 |
|-------------------------|------------------------------------|-------------------------------------------------------------------------------|
| `pageState`            | `PageState`                      | Indicates the current state of the page (e.g., loading, ready, etc.).         |
| `isProcessing`         | `boolean`                        | Tracks if a process is currently running.                                    |
| `isDisabled`           | `boolean`                        | Flags whether the page or controls are disabled.                             |
| `path`                 | `string`                         | Stores the path or URL for navigation or data fetching.                      |
| `entityName`           | `string`                         | Represents the name of the entity being managed or displayed.                |
| `appMenu`              | `AppMenuDto`                     | Contains menu details relevant to the application context.                   |
| `id`                   | `string`                         | Stores the unique identifier for the entity or item.                         |
| `item`                 | `ItemEntityDto`                  | Represents the current entity or item details.                               |
| `defaultItem`          | `ItemEntityDto`                  | Holds the default entity or item details.                                    |
| `pageTitle`            | `string`                         | The title displayed on the page.                                             |
| `pageSubTitle`         | `string`                         | The subtitle displayed on the page.                                          |
| `pageIcon`             | `string`                         | Icon representing the page or entity.                                        |
| `pageParams`           | `PageParams`                     | Parameters used to configure the page dynamically.                           |
| `xpgDetailsPageConfig` | `XpgDetailsPageConfig`           | Configuration for the details page, passed to the component dynamically.     |
| `pageMode`             | `'create' | 'update' | 'read'` | Determines the current page mode (create, update, or read).                  |
| `readMode`             | `boolean`                        | Indicates if the page is in read-only mode.                                  |
| `formGroup`            | `FormGroup`                      | Holds the form group for managing form controls and validations.             |
| `properties`           | `Property[]`                     | Lists the properties of the entity or form.                                  |
| `editProperties`       | `Property[]`                     | Specifies properties available for editing.                                  |
| `unique`               | `string[]`                       | Array of fields or properties marked as unique.                              |
| `cascadeProps`         | `{ fieldName: Property[] }`      | Holds cascade properties dependent on other fields.                          |
| `valueObjects`         | `{ fieldName: any }`             | Stores value objects for specific fields.                                    |
| `attachment`           | `{ [x: string]: FilePathDto }`   | Maps single attachments to their respective fields.                          |
| `attachments`          | `{ [x: string]: FilePathDto[] }` | Maps multiple attachments to their respective fields.                        |
| `selectOptions`        | `{ [x: string]: LookUpProp }`    | Holds options for dropdown or select fields.                                 |
| `selectEmptyOptions`   | `object[]`                       | Stores empty options for select fields.                                      |
| `destroy$`             | `Subject<void>`                  | Subject to manage the lifecycle of subscriptions.                            |
| `nameField`            | `string`                         | Specifies the name field of the entity.                                      |
| `codeField`            | `string`                         | Specifies the code field of the entity.                                      |
| `defaultPickerValue`   | `Date`                           | Default value for date picker fields.                                        |
| `shortcuts`            | `ShortcutInput[]`                | Stores keyboard shortcuts for the page.                                      |
| `downloading`          | `boolean`                        | Tracks if a file or data is being downloaded.                                |
| `items`                | `ItemEntityDto<string>[]`        | List of items/entities displayed or managed on the page.                     |
| `blockCancel`          | `boolean`                        | Flags whether cancel actions should be blocked.                              |

## Output
The <code>XPgDetailsComponent</code> is a dynamic Angular component designed for displaying and editing detailed information about selected items in the application. It provides a user-friendly interface for interacting with data, allowing users not only to view details but also to edit and save changes directly.  The <code>XPgDetailsComponent</code> is applied to manage the Fuel Parameter module in the GeoStem application.

![image](https://github.com/user-attachments/assets/2a63075d-df54-491a-8944-cf38f7d44f74)

- The <code>XPgDetailsComponent</code> is used to render the form on the right side of the image, which provides detailed information about a selected **fuel parameter**.
- Unlike read-only components, <code>XPgDetailsComponent</code> facilitates active user interaction. For instance, users can update fuel parameters (e.g., modifying the maximum density value) and save changes with the provided Save button.
- The <code>XPgDetailsComponent</code> ensures that all entities or parameters in the system use a consistent, reusable interface for managing their details. For example, other entities like Grade Groups or Sulphur could use the same component with their specific configurations.
- In the context of the image, the XPgDetailsComponent is applied to the Fuel Parameter module, enabling users to update properties such as Density @ 15°C, its Min/Max values, and associated configurations like GradeSpec or Link Code.
