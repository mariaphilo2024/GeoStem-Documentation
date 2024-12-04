# XPgReadComponent
<code>XPgReadComponent</code> is likely a reusable Angular component designed to display or manage "read" views of data, such as a detailed page or a readonly data view. It is dynamically loaded and configured through dependency injection, allowing it to adapt to specific contexts using provided parameters.
## Code Example

```typescript
this.component = XPgReadComponent;
this.injector = Injector.create({
  providers: [
    {
      provide: XPgReadParamProvider,
      useValue: new XPgReadParam(xPgReadPageConfig),
    },
  ],
  parent: this.inj,
});
```
- <code>**this.component**</code>: Assigns the XPgReadComponent to the component property.
- <code>**Injector.create**</code>: Creates a custom injector with the specified providers.
  
**Providers**:
- <code>**provide**</code>: Specifies the token (<code>XPgReadParamProvider</code>) for dependency injection.
- <code>**useValue**</code>: Passes a new instance of <code>XPgReadParam</code> initialized with xPgReadPageConfig.
- <code>**parent**</code>: Sets the parent injector to <code>this.inj</code>.
- <code>**useValue**</code>: Supplies a specific instance (<code>new XPgReadParam(xPgReadPageConfig</code>)) to be used whenever <code>XPgReadParamProvider</code> is requested.
- <code>**XPgReadParamProvider**</code> is a dependency injection token in Angular, used to supply a specific configuration or parameters (via <code>XPgReadParam</code>) to components like <code>XPgReadComponent</code>. It allows the component to receive context-specific data or settings dynamically at runtime.
-  <code>**XPgReadParam**</code> is a class  that holds configuration required by the <code>XPgReadComponent</code>. It encapsulates the necessary data, such as API configurations, UI settings, or other runtime information, which the component uses to render or behave dynamically based on the provided values.
