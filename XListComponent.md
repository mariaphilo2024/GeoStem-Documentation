# XListComponent
XListComponent is  designed to display and manage lists of data. It acts as a dynamic UI element, leveraging dependency injection (e.g., XListParam) to customize its behavior or data source.

## Code Example
```
 this.component = XListComponent;
    this.injector = Injector.create({
      providers: [
        {
          provide: XListParamProvider,
          useValue: new XListParam(xListInput),
        },
      ],
      parent: this.inj,
    });
```

### Component Assignment
- **<code>this.component</code>**:  Assigns the <code>XListComponent</code> class to the component property of the current class. It indicates that this property will hold a reference to the <code>XListComponent</code>.
### Injector Creation
- **<code>this.injector</code>**:  Creates a custom dependency injector using Angular's Injector.create() method. The injector is used to resolve and provide dependencies for components dynamically.
### Provider
- **<code>provide: XListParamProvider</code>**: Specifies the token <code>XListParamProvider</code> to identify the dependency.
- **<code>useValue: new XListParam(xListInput)</code>**: Creates a new instance of XListParam with the argument <code>xListInput</code>. This object is provided whenever <code>XListParamProvider</code> is requested.
### Parent Inlector
- Sets the <code>this.inj</code> (presumably an existing injector) as the parent for the newly created injector. This ensures that the new injector can inherit and resolve dependencies from its parent if not provided explicitly.
- **<code>XListParam</code>** is a class or object that holds configuration data or parameters for customizing the behavior of <code>XListComponent</code>.

 ## Properties of XListComponent:

| Property            | Type                          | Function                                      |
|---------------------|-------------------------------|----------------------------------------------|
| `xListInput`        | `XListInput`                 | Holds input data for the list component.     |
| `xListInputData`    | `XListInput`                 | Stores data for the list input.              |
| `entityName`        | `string`                     | Name of the entity being displayed.          |
| `items`             | `ItemEntityDto[]`            | List of all items.                           |
| `viewItems`         | `ItemEntityDto[]`            | Filtered or displayed items.                 |
| `showEditSidebar`   | `boolean`                    | Toggles the visibility of the edit sidebar.  |
| `blockClose`        | `boolean`                    | Prevents sidebar from closing.               |
| `xpgFormRef`        | `XFormComponent`             | Reference to the form component.             |
| `sidebarFullSize`   | `boolean`                    | Sets the sidebar to full size.               |
| `sidebarSize`       | `string`                     | Defines the size of the sidebar.             |
| `xpgEditComp`       | `Type<XFormComponent>`       | Type of the edit form component.             |
| `xpgEditInj`        | `Injector`                   | Injector for the edit component.             |
| `lookupFieldName`   | `string`                     | Field name for lookup operations.            |
| `currentUser$`      | `Observable<CurrentUserDto>` | Observable of the current user data.         |
| `isAdmin`           | `boolean`                    | Indicates if the current user is an admin.   |
| `filterObj`         | `PageFilterState`            | Object storing filter state.                 |
| `hasReadPolicy`     | `boolean`                    | Permission to read data.                     |
| `hasCreatePolicy`   | `boolean`                    | Permission to create new data.               |
| `hasEditPolicy`     | `boolean`                    | Permission to edit existing data.            |
| `hasDeletePolicy`   | `boolean`                    | Permission to delete data.                   |
| `filteredColumns`   | `XuiTableColumn[]`           | Columns displayed after filtering.           |
| `schemaStr`         | `EntitySchemaDto`            | Schema definition for the entity.            |
| `editProperties`    | `Property[]`                 | Properties available for editing.            |
| `globalFilterFields`| `string[]`                   | Fields used for global filtering.            |
| `tabComponent`      | `any`                        | Reference to the tab component.              |
| `tabInjector`       | `Injector`                   | Injector for the tab component.              |
| `expandRowProp`     | `Property`                   | Property for expanding rows.                 |
| `expandedRows`      | `{ [s: string]: boolean }`   | Tracks the expanded state of rows.           |
| `disableParentNav`  | `boolean`                    | Disables parent navigation if true.          |


