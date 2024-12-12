## XFormComponent📖
 `XFormComponent` purpose is to dynamically generate and manage forms based on backend API metadata or domain models. This Component utilized in `inquiry-broker` module.

 ### Code Example📝

 ```
loadComponent() {
    this.addBrokerButtonHidden = this.baseDetComponent.inquiryFuels.every(f => f.isBooked || f.isDelivered);
  }
newBrokerId: any;
  newBrokerFormId: any;
  xFormInput: XFormInput;
  xbrokerFormInput: XFormInput;
  xFormComponentPopRef: XFormComponent;
  showEmail: boolean;
  emailTemplateDto: EmailTemplateDto;
  addNewBroker() {
    this.brokerVisible = true;
    this.xFormInput = {
      entityName: 'broker',
      pageMode: 'create',
      hideSuccessMessage: true,
      saveText: 'Send For Approval',
      saveIcon: 'pi pi-send',
      columns: [
        { prop: 'name', hidden: false },
      ] as Property[],
      close: () => {
        this.brokerVisible = false;
      },
      onSave: (xFormResult: XFormResult) => {
        this.xFormInput.saveBtnTpl = this.brokerSaveBtnTpl;
        this.newBrokerId = xFormResult.id;
        this.sendBrokerApprovalEmail(this.newBrokerId);
      },

      onInit: (instance: XFormComponent) => {
        this.xFormComponentPopRef = instance;
      },
    } as XFormInput;
  }
```

- The `loadComponent()` method dynamically determines whether the "Add Broker" button should be visible based on the status of `inquiryFuels`. This ensures the button only appears when it is logical and necessary for the user to add a broker.
  
- The `addNewBroker` function is designed to facilitate the creation of a new broker entity in a dynamic and user-friendly way using the `XFormComponent`.
  
- `xFormComponentPopRef` is a variable of type `XFormComponent` that stores a reference to an initialized instance of the `XFormComponent`. This allows interaction with the component after it's created, such as accessing its methods or properties.
  
- The `addNewBroker()` method is called, making the form visible and configuring it dynamically.
  
- The form fields, buttons, and actions are dynamically controlled using `xFormInput`.
  
- `Entity Name`: Specifies that the form is for the `broker` entity.
  
- `onSave`: Executes after the form is submitted.Initiates an email approval workflow via `sendBrokerApprovalEmail`.
  
- `onInit`: Captures a reference to the initialized `XFormComponent` instance, stored in `xFormComponentPopRef`, for advanced interactions later.

  ### XFormComponent Properties:🧩

| **Property**         | **Type**                            | **Function**                                                              |
|-----------------------|-------------------------------------|---------------------------------------------------------------------------|
| `pageState`          | `PageState`                        | Tracks the current state of the page (e.g., loading, ready).              |
| `parentProcessing`   | `boolean`                          | Indicates if the parent component is in a processing state.               |
| `isProcessing`       | `boolean`                          | Indicates if the current component is processing.                         |
| `blockClose`         | `boolean`                          | Prevents the page from being closed when true.                            |
| `path`               | `string`                           | Stores the current path or route of the component.                        |
| `entityName`         | `string`                           | Represents the name of the entity being processed.                        |
| `appMenu`            | `AppMenuDto`                       | Stores application menu details.                                          |
| `id`                 | `string`                           | Holds the ID of the current entity.                                       |
| `item`               | `ItemEntityDto`                    | Represents the main entity being processed.                               |
| `defaultItem`        | `ItemEntityDto`                    | Stores a default version of the entity.                                   |
| `pageTitle`          | `string | null`                   | The title of the page, if any.                                            |
| `pageSubTitle`       | `string | null`                   | The subtitle of the page, if any.                                         |
| `pageIcon`           | `string`                           | Specifies the icon for the page.                                          |
| `pageParams`         | `PageParams | null`               | Stores parameters for the page.                                           |
| `pageMode`           | `PageMode | null`                | Indicates the mode of the page (e.g., edit, view).                        |
| `readMode`           | `boolean`                          | Indicates if the page is in read-only mode.                                |
| `formGroup`          | `FormGroup`                        | Manages the form controls and validations.                                |
| `properties`         | `Property[]`                       | Lists the properties of the entity.                                       |
| `editProperties`     | `Property[]`                       | Lists the editable properties of the entity.                              |
| `unique`             | `string[]`                         | Tracks unique properties of the entity.                                   |
| `valueObjects`       | `{ [x: string]: any }`             | Holds value objects for the entity.                                       |
| `cascadeProps`       | `{ [x: string]: Property[] }`      | Defines cascading properties based on conditions.                         |
| `requiredIfProps`    | `{ [x: string]: RequiredIfProp[] }`| Lists properties required based on specific conditions.                   |
| `readOnlyIfProps`    | `{ [x: string]: ReadOnlyIfProp[] }`| Lists properties that become read-only based on conditions.               |
| `attachment`         | `{ [x: string]: FilePathDto }`     | Represents a single file attachment for specific fields.                  |
| `attachments`        | `{ [x: string]: FilePathDto[] }`   | Represents multiple file attachments for specific fields.                 |
| `selectEmptyOptions` | `Array<object>`                    | Placeholder for empty select options.                                     |
| `selectOptions`      | `{ [x: string]: LookUpProp }`      | Stores lookup options for dropdown fields.                                |
| `destroy$`           | `Subject<void>`                    | Observable to manage component destruction.                               |
| `nameField`          | `string`                           | Holds the name field of the entity.                                       |
| `codeField`          | `string`                           | Holds the code field of the entity.                                       |
| `defaultPickerValue` | `Date`                             | Represents the default value for a date picker.                           |
| `shortcuts`          | `ShortcutInput[]`                  | Stores keyboard shortcuts for the component.                              |
| `downloading`        | `boolean`                          | Indicates if a download operation is in progress.                         |
| `items`              | `ItemEntityDto<string>[]`          | Represents a collection of entity items.                                  |
| `blockCancel`        | `boolean`                          | Prevents cancel actions when true.                                        |
| `loadingPic`         | `boolean`                          | Indicates if a picture is currently loading.                              |
| `pictureSrc`         | `string`                           | Stores the source URL of the picture.                                     |
| `hasPicture`         | `boolean`                          | Indicates if the entity has an associated picture.                        |
| `hasPictureTpl`      | `TemplateRef<any>`                 | Template reference for displaying pictures.                               |
| `disableAutofocus`   | `boolean`                          | Disables autofocus on form fields when true.                              |


## OutPut

![image](https://github.com/user-attachments/assets/26eb91a8-b8aa-4823-8af8-5962214d2018)
