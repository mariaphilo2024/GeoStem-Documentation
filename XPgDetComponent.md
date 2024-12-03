# XPgDetComponent
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
```
 ### Assigning Component:

- <code>this.component = XPgListComponent;</code>: Specifies <code>XPgListComponent</code> as the component to be loaded.
Creating Injector:
- <code>Injector.create</code>: Dynamically creates a new Injector instance.
  
 ### Providers:

- The <code>Injector</code> is configured with a provider for <code>XPgListParamProvider</code>.
- The <code>useValue</code> parameter passes a new instance of <code>XPgListParam</code>.
 ### XPgListParam Configuration:

- <code>entityName</code>: Specifies the entity name as 'template'.
- <code>detailsComp</code>: Sets <code>TemplateDetComponent</code> as the detailed component.
- <code>onInit</code>: Provides an optional initialization callback function for <code>XPgListComponent</code>.
- <code>sidebarFullSize</code>: A boolean to configure the sidebar's size.
  ### Parent Injector:

- parent: <code>this.inj</code>: Sets the existing Injector as the parent for the newly created one.
