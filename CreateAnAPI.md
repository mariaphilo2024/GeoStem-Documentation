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

**Step 2: Add a DbSet for Country in DbContext in EntityFrameWorkCore**

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

**Strep 3: Add a configuration for the Country entity to specify the table name and any conditions.**
```
builder.Entity<Country>(b =>
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
**Step 4: Configure the Database Connection String in appsettings.json** 
- Add or update the ConnectionStrings section to include the database connection string.
```
{
    "ConnectionStrings": {
        //DO NOT COMMIT THIS FILE, IF CHANGED!!
        "Default": "Server=localhost\\SQLEXPRESS;Database=GeoStem;Trusted_Connection=True;TrustServerCertificate=True"
    },
}
```
**Step 5: Create the Migration**
- Right click on **GeoStem.DbMigrator** project and select **Set as StartUp Project**
- Open **Package Manager Console**.
- Select **EntityFrameworkCore** as a default file.
- Add command 'Add-Migration' "Create-Country"
- Run the project.
  In this step migration files will be created.

**Step 6: Create DTOs for Country in GeoStem.Application.Contracts**
- DTOs act as a protective layer between the database and the API consumers, ensuring that changes to the database schema do not directly impact the API contracts.
- DTOs are useful for validating input data when creating or updating records.
- create a folder named Countries.
- create a file named CountryDto.cs.

```
  
  namespace GeoStem.Countries
{
    public class CountryDto : AuditedEntityDto<Guid>, IHasConcurrencyStamp, IHasActive
    {
        public string Code { get; set; }
        public string Name { get; set; }
        public Guid? ContinentId { get; set; }
        public virtual IdNameDto Continent { get; set; }
        public Guid? CurrencyId { get; set; }
        public virtual IdNameDto Currency { get; set; }
        public bool Active { get; set; }
        public string ConcurrencyStamp { get; set; }
    }
     public class CountryListDto : EntityDto<Guid>
 {
     public string Code { get; set; }
     public string Name { get; set; }
     public string ContinentName { get; set; }
     public string CurrencyName { get; set; }
     public bool Active { get; set; }     
 }
  public class CreateCountryDto
 {
     [Required]
     [StringLength(12)]
     [MinLength(3)]
     public string Code { get; set; }

     [Required]
     [StringLength(100)]
     [MinLength(3)]
     public string Name { get; set; }
     [Required]
     public Guid? ContinentId { get; set; }

     [Required]
     public Guid? CurrencyId { get; set; }

     [DefaultValue(true)]
     public bool Active { get; set; }

 }
     public class UpdateCountryDto : CreateCountryDto
    {

    }
}
```

**Step 7: Add Mapping for Country in GeoStem.Application**
- Open GeoStemApplicationAutoMapperProfile.cs file
- Add Mapping for Country

```
       CreateMap<Country, CountryDto>().ReverseMap();
        CreateMap<Country, CountryListDto>().ReverseMap();
        CreateMap<CreateCountryDto, Country>();
        CreateMap<UpdateCountryDto, Country>();
```   

**Step 8: Manage Permission for CountryMaster API in GeoStem.Application.Contracts**
- Go to the Permissions folder
- Open a file named GeneralMasterPermission.cs.
- Add a Permission for CountryMaster.
  
  **Step 9: Register Master Permission in GeoStem.Application**
- Go to Countries folder
- Open CounrtService.cs
- Register MasterPermission for countries.

```
  namespace GeoStem.Countries
{
    public class CountryService : BasePageService<Country, CountryDto, CreateCountryDto, UpdateCountryDto, CountryListDto, PageRequestDto>
    {
        public CountryService(IRepository<Country, Guid> repository)
            : base(repository)
        {
            GetPolicyName = GeographyMasterPermissions.Countries.Default;
            GetListPolicyName = GeographyMasterPermissions.Countries.Default;
            CreatePolicyName = GeographyMasterPermissions.Countries.Create;
            UpdatePolicyName = GeographyMasterPermissions.Countries.Edit;
            DeletePolicyName = GeographyMasterPermissions.Countries.Delete;
        }
```

**Step 10: Create API endpoints to perform CRUD operations on Country.** 
- Go to GeoStem.HttpApi.Host
- Right click on, Select Set as Starup Project
- Run the Project.

![image](https://github.com/user-attachments/assets/1b5119d7-0d48-4933-8f74-68b0f4617c18)
![image](https://github.com/user-attachments/assets/3a75bc2d-42b5-4b6c-b262-34839601a784)
![image](https://github.com/user-attachments/assets/30fadd58-ea77-46ce-9366-59879d4170b3)



    
    






    


