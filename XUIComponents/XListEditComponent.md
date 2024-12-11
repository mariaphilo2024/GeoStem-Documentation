## XListEditComponent📖
The purpose of `XListEditComponent` is to manage "list-edit" operations, providing a unified and dynamic interface for editing collections of items related to a specific backend API.

### Code Example📝
```
 this.addtlCostComponent = XListEditComponent;
    this.addtlCostInjector = Injector.create({
      providers: [
        {
          provide: XListParamProvider,
          useValue: new XListParam({
            entityName: 'invoice-additional-cost',
            tableWrapperClass: 'overflow-y-auto',
            parentPageMode: parentPageMode,
            columns: [
              { prop: 'inquiryDetailId', defaultValue: this.xpDetRef.id },
              { prop: 'invoiceCustomerId', defaultValue: row.id },
              { prop: 'inquiryFuelDetailId', defaultValue: row.inquiryFuelDetailId },
               ] as Property[],
            items: items,
            isRowReadOnly: (row: InvoiceAdditionalCostDto, formGroup) => {
              return parentPageMode === 'read';
            },
            onInit: (instance: XListEditComponent) => {
              this.addtlCostRef = instance;
              this.addtlCostLoading = false;
            },
            pageTitle: `Additional Cost  (${inquiryFuel.description})`,
          } as XListInput),
        },
      ],
      parent: this.inj,
    });
```

### Component Assignment:
- `this.addtlCostComponent` Assigns XListEditComponent to addtlCostComponent, indicating that this component will be dynamically loaded. 

### Injector Creation:
- `this.addtlCostInjector = Injector.create`: Creates a custom injector for dynamically configuring and providing dependencies to the `XListEditComponent`.

### Providers:
- `XListParamProvider`: Supplies configuration parameters (`XListParam`) to the component.
- `useValue`: Provides an instance of `XListParam` with specific settings.

 ### Configuration via XListParam:
- `entityName`: Specifies the entity to manage, in this case, `invoice-additional-cost`.
- `tableWrapperClass`: Defines CSS classes for styling the component's table, allowing vertical scrolling (`overflow-y-auto`).
- `parentPageMode`: A mode (e.g., 'edit', 'read') that controls component behavior.

  ### Initialization Callback:
 -  Executes when the component is initialized:
       - Saves the component instance to addtlCostRef.
       - Sets addtlCostLoading to false, indicating the component is ready.

 ### Parent Injector:
 - Establishes `this.inj` as the parent injector, enabling hierarchical dependency injection.



