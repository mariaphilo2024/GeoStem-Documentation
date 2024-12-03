# Template Component Using XUI in the GEOSTEM Project

 

# Dynamic Component Initialization with Injector

This snippet demonstrates how to initialize a component dynamically using the `Injector.create()` method in Angular.

## Code Example

```typescript
this.component = XPgListComponent;
this.injector = Injector.create({
  providers: [
    {
      provide: XPgListParamProvider,
      useValue: new XPgListParam({
        entityName: 'template',
        detailsComp: TemplateDetComponent,
        onInit: (instance: XPgListComponent) => {},
        sidebarFullSize: true,
      } as XpgListPageConfig),
    },
  ],
  parent: this.inj,
});

The XPgListComponent is assigned to this.component, indicating the dynamic component to be loaded.
The providers array specifies dependencies injected into the component.

XPgListParamProvider: This is provided with a value of a new instance of XPgListParam.
XPgListParam Configuration:
entityName: Specifies the entity, here set to 'template'.
detailsComp: Indicates the component for detailed views, here TemplateDetComponent.
onInit: A callback invoked when the XPgListComponent instance is initialized.
sidebarFullSize: A boolean flag for sidebar settings, set to true.
# `XpgListPageConfig` Interface

The table below provides details of the properties in the `XpgListPageConfig` interface.

| **Property**           | **Type**                      | **Description**                                                                 |
|-------------------------|-------------------------------|---------------------------------------------------------------------------------|
| `entityName`           | `string`                     | Name of the entity associated with the list.                                   |
| `columns`              | `Property[]`                 | Optional array defining the columns in the list.                               |
| `onInit`               | `(instance?: any) => void`   | Callback executed during component initialization.                             |
| `onListChange`         | `() => void`                 | Optional callback triggered when the list changes.                             |
| `readComp`             | `Type<any>`                 | Optional component for read-only views.                                        |
| `detailsComp`          | `Type<any>`                 | Optional component for displaying item details.                                |
| `sidebarFullSize`      | `boolean`                   | Determines if the sidebar should be full size.                                 |
| `parentEntity`         | `string`                    | Name of the parent entity.                                                     |
| `parentId`             | `string`                    | ID of the parent entity.                                                       |
| `parentProp`           | `string`                    | Property linking the child entity to the parent.                               |
| `parentPageMode`       | `PageMode`                  | Mode of the parent page.                                                       |
| `parentItem`           | `any`                       | Data of the parent entity.                                                     |
| `filterTpl`            | `TemplateRef<any>`          | Optional template for the filter.                                              |
| `filterBeforeTpl`      | `TemplateRef<any>`          | Template displayed before the filter.                                          |
| `afterActionTemplate`  | `TemplateRef<any>`          | Template displayed after an action is performed.                               |
| `headerTpl`            | `TemplateRef<any>`          | Template for the page header.                                                  |
| `replaceTitleTpl`      | `TemplateRef<any>`          | Optional template to replace the default title.                                |
| `staticFilter`         | `string`                    | Optional static filter applied to the list.                                    |
| `update`               | `(row: any) => void`        | Optional function to update a row.                                             |
| `read`                 | `(row: any) => void`        | Optional function to read a row's data.                                        |
| `onDataRequest`        | `(query: any) => any`       | Callback for handling data requests.                                           |
| `replaceListTpl`       | `TemplateRef<any>`          | Optional template to replace the default list view.                            |
| `requestMethod`        | `string`                    | HTTP method for data requests (e.g., `GET`, `POST`).                           |
| `disablePaginator`     | `boolean`                   | Flag to disable pagination.                                                    |
| `enableCheckBox`       | `boolean`                   | Flag to enable checkboxes in the list.                                         |
| `editableRows`         | `boolean`                   | Flag to make rows editable.                                                    |
| `checkboxTpl`          | `TemplateRef<any>`          | Template for custom checkboxes.                                                |
| `rowClass`             | `{ [x: string]: string }`   | Class mappings for row customization.                                          |

## Example Usage

```typescript
const listPageConfig: XpgListPageConfig = {
  entityName: 'exampleEntity',
  columns: [
    { name: 'Column 1', type: 'string' },
    { name: 'Column 2', type: 'number' },
  ],
  onInit: (instance) => {
    console.log('List initialized:', instance);
  },
  detailsComp: ExampleDetailsComponent,
  sidebarFullSize: true,
  filterBeforeTpl: myFilterBeforeTemplate,
  afterActionTemplate: myAfterActionTemplate,
};
