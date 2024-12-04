# XPgDetailsComponent
The <code>XPgDetailsComponent</code> is a dynamic Angular component designed to display detailed information about a specific item or entity. It is highly configurable, leveraging injected parameters (e.g., <code>XPgDetailsParam)</code> to customize its behavior and content at runtime. This makes it reusable and adaptable for various use cases where detailed entity views are required.
## Code Example

```typescript
this.component = XPgDetailsComponent;
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
