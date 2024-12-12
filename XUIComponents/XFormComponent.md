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
