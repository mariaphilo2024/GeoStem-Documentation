## XFormComponent📖
 `XFormComponent` purpose is to dynamically generate and manage forms based on backend API metadata or domain models. This Component utilized in `inquiry-broker` module.

 Code Example📝

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
- The `addNewBroker` function is designed to facilitate the creation of a new broker entity in a dynamic and user-friendly way using the `XFormComponent`
- `xFormComponentPopRef` is a variable of type `XFormComponent` that stores a reference to an initialized instance of the `XFormComponent`. This allows interaction with the component after it's created, such as accessing its methods or properties.
- The `addNewBroker()` method is called, making the form visible and configuring it dynamically.
- The form fields, buttons, and actions are dynamically controlled using `xFormInput`.
- `Entity Name`: Specifies that the form is for the `broker` entity.
- `onSave`: Executes after the form is submitted.Initiates an email approval workflow via sendBrokerApprovalEmail
- `onInit`: Captures a reference to the initialized `XFormComponent` instance, stored in `xFormComponentPopRef`, for advanced interactions later.
