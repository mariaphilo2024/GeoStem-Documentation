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

## XListEditComponent Properties:

| Property              | Type                        | Function                                                                 |
|-----------------------|-----------------------------|--------------------------------------------------------------------------|
| RowStatus            | `RowStatus`                | Represents the status of a row.                                         |
| formGroup            | `FormGroup`                | Handles form controls and validation.                                   |
| entityName           | `string`                   | Stores the name of the entity being managed.                            |
| items                | `ItemEntityDto[]`          | List of item entities being displayed or managed.                       |
| viewItems            | `ItemEntityDto[]`          | Filtered or processed items for display.                                |
| showEditSidebar      | `boolean`                  | Indicates whether the edit sidebar is visible.                          |
| blockClose           | `boolean`                  | Prevents sidebar closing if set to true.                                |
| xpgFormRef           | `XFormComponent`           | Reference to the form component used for editing.                       |
| sidebarFullSize      | `boolean`                  | Determines whether the sidebar is displayed in full size.               |
| xpgEditComp          | `Type<XFormComponent>`     | Type of the edit component being used.                                  |
| xpgEditInj           | `Injector`                 | Injector for providing dependencies to the edit component.              |
| lookupFieldName      | `string`                   | Specifies the field name used for lookup operations.                    |
| currentUser$         | `Observable<CurrentUserDto>` | Observable for the current user's data.                                |
| isAdmin              | `boolean`                  | Indicates if the current user has admin privileges.                     |
| filterObj            | `PageFilterState`          | Represents the state of page-level filters.                             |
| hasCreatePolicy      | `boolean`                  | Determines if the user can create new entries.                          |
| hasEditPolicy        | `boolean`                  | Determines if the user can edit existing entries.                       |
| hasDeletePolicy      | `boolean`                  | Determines if the user can delete entries.                              |
| filteredColumns      | `XuiTableColumn[]`         | Stores the columns currently being displayed after filtering.           |
| schemaStr            | `EntitySchemaDto`          | Schema definition of the entity.                                        |
| tabComponent         | `any`                      | Component used for tab-based navigation or display.                     |
| tabInjector          | `Injector`                 | Injector for providing dependencies to the tab component.               |
| expandRowProp        | `Property`                 | Property that defines which rows are expandable.                        |
| expandedRows         | `{ [s: string]: boolean }` | Tracks which rows are currently expanded.                               |
| isReadOnly           | `boolean`                  | Indicates whether the page is in read-only mode.                        |
| pageState            | `PageState`                | Represents the current state of the page.                               |
| pageTitle            | `string`                   | Title of the page.                                                      |
| viewDetailsTemplate  | `TemplateRef<any>`         | Template reference for viewing details.                                 |
| enumViewDetailsTemplate | `TemplateRef<any>`      | Template reference for viewing enumerated details.                      |
| actionTemplate       | `TemplateRef<any>`         | Template reference for action buttons or controls.                      |
| dataTable            | `Table`                    | Reference to the data table component.                                  |
| settingsMenu         | `Menu`                     | Reference to the settings menu component.                               |
| filterMenuRef        | `Menu`                     | Reference to the filter menu component.                                 |
| enumLabels           | `{ fieldName: string[] }`  | Stores labels for enumerated fields.                                    |
| editProperties       | `Property[]`               | List of properties available for editing.                               |
| selected             | `ItemEntityDto[]`          | Array of currently selected items.                                      |
| selectAllRowsOnPage  | `boolean`                  | Indicates if all rows on the current page are selected.                 |
| selectedId           | `string`                   | ID of the currently selected item.                                      |
| selectedItem         | `ItemEntityDto`            | The currently selected item entity.                                     |
| filteredViewItems    | `[]`                       | Array of items after applying filters.                                  |
| tableOptions         | `{ columns: XuiEditTableColumn[]; selectedColumns: XuiEditTableColumn[]; sorts?: any[]; }` | Options for configuring the table display and behavior. |
| quickSearchValue     | `any`                      | Current value for the quick search filter.                              |
| quickSearchMin       | `number`                   | Minimum value for the quick search range filter.                        |
| quickSearchMax       | `number`                   | Maximum value for the quick search range filter.                        |
| listWithOutDetails   | `boolean`                  | Indicates if the list should be displayed without additional details.   |
| selectedFilterItem   | `XuiTableColumn`           | Currently selected filter column.                                       |
| filterColumns        | `MenuItem[]`               | List of menu items available for filtering.                             |
| showOnlyInactive     | `boolean`                  | Indicates if only inactive items should be shown.                       |
| statusOptionValue    | `string`                   | Current status option value (e.g., 'active', 'inactive').               |
| statusOptions        | `any[]`                    | List of available status options.                                       |
| activeFilter         | `boolean`                  | Indicates if the active filter is applied.                              |
| readNavPath          | `string`                   | Navigation path for read operations.                                    |
| dateDisplayFormat    | `string`                   | Format used for displaying dates.                                       |
| defaultPickerValue   | `Date`                     | Default date value for date pickers.                                    |


