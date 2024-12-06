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

    


