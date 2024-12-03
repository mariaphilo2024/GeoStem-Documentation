# XPgDetComponent
## Code Example

```typescript
this.component = XPgDetComponent;
this.injector = Injector.create({
  providers: [
    {
      provide: XPgDetailsParamProvider,
      useValue: new XPgDetailsParam(xpgDetailsPageConfig),
    },
  ],
  parent: this.inj,
});
```
### Component Assignment:

- The component <code>XPgDetComponent</code> is assigned to the component property.
### Injector Creation:

- Create a new Injector using  <code>Injector.create()</code>.
- The providers array contains a provider for  <code>XPgDetailsParamProvider</code>, which uses the value of a new XPgDetailsParam initialized with  <code>xpgDetailsPageConfig</code>.
### Parent Injector:

- The parent injector is set to  <code>this.inj</code>, which indicates the parent context for dependency resolution.

### XPgDetailsParamProvider
An abstract class used as a base for providing details page parameters. It holds the <code>xpgDetailsPageConfig</code> object, which contains configuration settings and callbacks for the detail page.
### XPgDetailsParam
- A concrete class extending <code>XPgDetailsParamProvider</code>. It provides a specific implementation of the <code>XPgDetailsParamProvider</code> service, initialized with <code>xpgDetailsPageConfig</code>. This class is used to pass configuration details to the component.
 ### XpgDetailsPageConfig
-  An interface defining the structure and properties required for configuring the details page. It includes various settings such as <code>entityName</code>, <code>columns</code>, <code>onInit</code>, <code>close</code>, <code>save</code>, and several other optional properties. This interface is used to set up the detail page and control its behavior within the <code>XPgDetComponent</code>.



 
