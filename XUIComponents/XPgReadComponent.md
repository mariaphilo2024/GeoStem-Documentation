# XPgReadComponent📖
<code>XPgReadComponent</code> is likely a reusable Angular component designed to display or manage "read" views of data, such as a detailed page or a readonly data view. It is dynamically loaded and configured through dependency injection, allowing it to adapt to specific contexts using provided parameters.
## Code Example📝

```typescript
this.component = XPgReadComponent;
this.injector = Injector.create({
  providers: [
    {
      provide: XPgReadParamProvider,
      useValue: new XPgReadParam(xPgReadPageConfig),
    },
  ],
  parent: this.inj,
});
```
**Component Assignment**
- <code>**this.component**</code>: Assigns the XPgReadComponent to the component property.
 
**Injector Creation**
- <code>**Injector.create**</code>: Creates a custom injector with the specified providers.
  
**Providers**:
- <code>**provide**</code>: Specifies the token (<code>XPgReadParamProvider</code>) for dependency injection.
- <code>**useValue**</code>: Passes a new instance of <code>XPgReadParam</code> initialized with xPgReadPageConfig.
- <code>**parent**</code>: Sets the parent injector to <code>this.inj</code>.
- <code>**useValue**</code>: Supplies a specific instance (<code>new XPgReadParam(xPgReadPageConfig</code>)) to be used whenever <code>XPgReadParamProvider</code> is requested.
- <code>**XPgReadParamProvider**</code> is a dependency injection token in Angular, used to supply a specific configuration or parameters (via <code>XPgReadParam</code>) to components like <code>XPgReadComponent</code>. It allows the component to receive context-specific data or settings dynamically at runtime.
-  <code>**XPgReadParam**</code> is a class  that holds configuration required by the <code>XPgReadComponent</code>. It encapsulates the necessary data, such as API configurations, UI settings, or other runtime information, which the component uses to render or behave dynamically based on the provided values.

  ## Properties of XpgReadPageConfig:🧩

| **Property**         | **Type**                     | **Function**                                                                 |
|-----------------------|------------------------------|-------------------------------------------------------------------------------|
| `pageState`          | `PageState`                 | Tracks the current page state (e.g., loading, loaded).                      |
| `isProcessing`       | `boolean`                   | Indicates whether a process is ongoing.                                     |
| `path`               | `string`                    | Represents the current page or entity path.                                 |
| `entityName`         | `string`                    | Stores the name of the entity being managed.                                |
| `appMenu`            | `AppMenuDto`                | Holds menu configuration for the application.                              |
| `id`                 | `string`                    | Unique identifier for the current item.                                     |
| `item`               | `ItemEntityDto`             | The main item data entity for the page.                                     |
| `defaultItem`        | `ItemEntityDto`             | Stores the default values for the item entity.                              |
| `pageTitle`          | `string`                    | The title displayed on the page.                                            |
| `pageSubTitle`       | `string`                    | A subtitle displayed below the page title.                                  |
| `pageIcon`           | `string`                    | Icon associated with the page.                                              |
| `pageParams`         | `PageParams`                | Parameters or settings for the page.                                        |
| `xpgReadPageConfig`  | `XPgReadPageConfig`         | Configuration specific to the `XPgReadComponent`.                           |
| `pageMode`           | `'create' | 'update' | 'read'` | Defines the operational mode of the page (create, update, or read).          |
| `formGroup`          | `FormGroup`                 | Angular `FormGroup` for managing form controls.                             |
| `properties`         | `Property[]`               | A list of general properties for the entity.                                |
| `editProperties`     | `Property[]`               | A subset of properties editable in the form.                                |
| `destroy$`           | `Subject<void>`             | Used for unsubscribing from observables to prevent memory leaks.            |
| `nameField`          | `string`                    | The name field of the entity.                                               |
| `codeField`          | `string`                    | The code field of the entity.                                               |
| `defaultPickerValue` | `Date`                      | Default value for date picker components.                                   |
| `shortcuts`          | `ShortcutInput[]`          | Defines keyboard shortcuts for the page.                                    |
| `downloading`        | `boolean`                   | Indicates whether a file or resource is being downloaded.                   |

## Output
<code>XPgReadComponent</code> is used for displaying or managing detailed, read-only views of data, with dynamic configuration provided via dependency injection.
![image](https://github.com/user-attachments/assets/4e3de9b2-a10e-4311-942b-e4be589db923)
- In the example shown the <code>XPgReadComponent</code> is used in the agent-read.component .ts to display comprehensive details about an agent. The page includes multiple sections such as personal information, ports, bank accounts, and contact information.
- **Agent Details**: On the left, the agent's personal information including name, status, address, country, phone number and email is displayed.
- **Tabs and Sections**: The main section includes tabs for Ports, Bank Accounts, and Contact Information. Each tab provides relevant details in a structured format. For example, the Bank Accounts tab lists multiple bank accounts with detailed information about each account.
- **UI Elements**: The page includes various UI elements like tables, tabs, and informational panels to enhance the readability and usability of the information.

