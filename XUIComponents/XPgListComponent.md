# XPgListComponent📖 

<code>XPgListComponent</code> is a dynamic, reusable Angular component designed to render list-based views for entities. It integrates with configuration options like entity name, detail components, and callbacks to customize behavior and layout. Ideal for rapid UI generation, it supports dependency injection for flexible use in various contexts.
 

## Code Example📝

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
```

+ The <code>XPgListComponent</code> is assigned to this.component, indicating the dynamic component to be loaded.
- The providers array specifies dependencies injected into the component.

- <code>XPgListParamProvider</code>: This is provided with a value of a new instance of XPgListParam.
XPgListParam Configuration:
- Creates a new Injector instance using <code>Injector.create</code>.
- The <code>useValue</code> parameter passes a new instance of XPgListParam.
* <code>entityName</code>: Specifies the entity, here set to 'template'.
- <code>detailsComp</code>: Indicates the component for detailed views, here <code>TemplateDetComponent</code>.
- <code>onInit</code>: A callback invoked when the <code>XPgListComponent</code> instance is initialized.
- <code>sidebarFullSize</code>: Configures the size of the sidebar.
- <code>parent: this.inj</code>: Sets the existing <code>Injector</code> as the parent for the newly created one.
## `XpgListPageConfig` Interface:🧩

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

<h2>Output</h2>

<p><strong>Templates  Overview</strong></p>
A screenshot from the GeoStem application, specifically showing a list of email templates available in the Templates section under the System menu.

![image](https://github.com/user-attachments/assets/0705e592-118d-4756-b98b-1b1816527a35)


- **Actions**: Includes icons for editing or deleting templates.
- **Code**: Unique identifier for each template (e.g., TPL10496).
- **Name**: Descriptive name of the template (e.g., BrokerRejectedMail).
- **Type**: Format of the template (e.g., html).
- **Subject**: Subject line of the template email (e.g., BrokerRejectedMail:DefaultSubject).

 ### Purpose of the Templates Module
The Templates section in the GeoStem application is likely used to:

- Manage pre-configured email templates.
- Automate communication processes by using templates for notifications, approvals, rejections, etc.
- Define email content with placeholders ({{model.job_no}}, {{model.customer}}) that dynamically populate data during runtime.
