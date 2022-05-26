# Solution Architecture
* [Patterns & Practices - Introduction](https://docs.microsoft.com/en-us/archive/msdn-magazine/2009/may/patterns-and-practices-simplifying-patterns-and-practices)
* System design
* [Design patterns](https://youtu.be/0jjNjXcYmAU)
    * Abstract
    * Facade
    * [Idempotency Pattern](https://blog.jonathanoliver.com/idempotency-patterns/)
* Integration pattern - Messaging (Queue, Pub-Sub), API based
* SOLID principle
* [REST Maturity Model](https://martinfowler.com/articles/richardsonMaturityModel.html) - Richardson Maturity Model (RMM) breaks down the principal elements of a REST approach into three steps. These introduce resources, http verbs, and hypermedia controls (HATEOAS - Hypertext As The Engine Of Application State)
    * Level 0 - Simply calling a remote service over URL 
    * Level 1 - Introduce resources
    * Level 2 - Introduce operations
    * Level 3 - Provide the URI for the next set of associated resources in the body of the response
* [REST vs SOAP](https://www.upwork.com/hiring/development/soap-vs-rest-comparing-two-apis/) - REST API architectural style, light, fast, JSON, broadly accepted; SOAP - XML based, heavy, slower, xml schema, SOA architecture - [REST popularity](https://www.quora.com/Why-is-REST-becoming-more-popular-than-SOAP-these-days)
* [REST API - large binary files](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design#support-partial-responses-for-large-binary-resources)
* [REST API versioning](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design#versioning-a-restful-web-api) - URI versioning, Header versioning
* TOGAF framework
* [DDD - Domain-Driven Design Pattern](https://en.wikipedia.org/wiki/Domain-driven_design) - Approach to create [domain models](https://martinfowler.com/eaaCatalog/domainModel.html) that reflect the business processes and use cases. It's a vast concept but in simple terms, creating a model based on business problems as domains. 
* [CQRS - Command & Query Responsibility Segregation Pattern](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns)