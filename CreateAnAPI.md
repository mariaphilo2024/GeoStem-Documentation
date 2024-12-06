### Create an API
An **API** (Application Programming Interface) is a set of rules and protocols that allows one software application to interact with another. They enable different applications, services, or platforms to communicate and work together, even if they’re built on different technologies.

Most common types of APIs. 
- **Web APIs**: APIs designed to be accessed over the web, typically using **HTTP**.

 - **Database API**: Is an interface that allows applications to interact with a database programmatically. 
 
- **Operating System APIs**: APIs provided by operating systems for application development.
 - **Library or Framework APIs**: APIs exposed by libraries or frameworks for specific functionality.
 

Here are the steps to create an API for **Country**. 

 **Step1: Create the Country folder and class in the Domain layer.** 

 ```
namespace GeoStem.Countries
{
    [Audited]
    public class Country : FullAuditedAggregateRoot<Guid>, IHasActive, IHasName, IHasAllRecord
    {
        public Country() { /* This constructor is used by the ORM/database provider */ }
        public Country(Guid id) : base(id)
        {
        }
        public string Code { get; set; }

        public string Name { get; set; }
        public Guid? ContinentId { get; set; }
        public virtual Continent Continent { get; set; }
        public Guid? CurrencyId { get; set; }
        public virtual Currency Currency { get; set; }
        public bool Active { get; set; }
    }
}
```

**Step 2 Add a DbSet for Country in DbContext in EntityFrameWorkCore**

```public class GeoStemDbContext :
    AbpDbContext<GeoStemDbContext>,
    IIdentityDbContext,
    ITenantManagementDbContext
{
    /* Add DbSet properties for your Aggregate Roots / Entities here. */
    public DbSet<Continent> Continents { get; set; }
    public DbSet<Currency> Currencies { get; set; }
    public DbSet<Country> Countries { get; set; }
```
In the **DbContext class**, add a **DbSet** property for the Country entity. This will enable Entity Framework Core to track and manage Country entities and will map it to a Countries table in the database.

```  builder.Entity<Country>(b =>
  {
      b.ToTable(GeoStemConsts.DbTablePrefix + "Countries",
         GeoStemConsts.DbSchema);
      b.ConfigureByConvention(); //auto configure for the base class props
      b.Property(x => x.Name).IsRequired().HasMaxLength(100);
      b.Property(x => x.Code).IsRequired().HasMaxLength(12);
      b.HasIndex(u => u.Name).IsUnique();
      b.HasIndex(u => u.Code).IsUnique();

      b.HasOne(c => c.Currency).WithMany().HasForeignKey(x => x.CurrencyId);
      b.HasOne(c => c.Continent).WithMany().HasForeignKey(x => x.ContinentId);
  });
```


    


