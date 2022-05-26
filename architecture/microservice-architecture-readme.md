# Microservice Architecture
* [Design patterns for microservice architecture](https://docs.microsoft.com/en-us/azure/architecture/microservices/design/patterns)
    * [Common Cloud Design Patterns](https://levelup.gitconnected.com/cloud-design-patterns-explained-simply-113c788b33ff)
* [Design patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/)
* [Microservice Reference Architecture](https://github.com/dotnet-architecture/eShopOnContainers)
* [CNCF - Cloud Native Trail Map](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) - Containerization is the first step in CNCF trail map.
* [Challenges with Monolithic services](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/leverage-containers-orchestrators#challenges-with-monolithic-deployments) - Deployments, scaling, environment dependencies, tight coupling, platform lock-in (opposite of polyglot)
* [Containers & Orchestrators](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/leverage-containers-orchestrators#what-are-the-benefits-of-containers-and-orchestrators)
* [Migrating Monolith application to Microservices](https://martinfowler.com/articles/break-monolith-into-microservices.html)
    1. Lay the groundwork like Infrastructure, automated CI/CD pipeline, API Mgmt for routing, throttling, versioning.
    2. Start with a simple decoupled functionality, may be an edge service like authentication service.
    3. Decouple capabilities which are dependent service first. For e.g., between order depends on promotion functionality, so move the promotion functionality to microservice first as this will reduce the dependency on the monolith application.  
    4. It may not always be possible to avoid dependencies back to the monolith. In cases where a new service ends up with a call back to the monolith, it is suggested to expose a new API from the monolith, and access the API through an [anti-corruption layer](https://docs.microsoft.com/en-us/azure/architecture/patterns/anti-corruption-layer) in the new service to make sure that the monolith concepts do not leak out.  
    ![Alt text](/images/preferred-dependency.jpg)    
    5. [Split Sticky Capabilities](https://martinfowler.com/articles/break-monolith-into-microservices.html#SplitStickyCapabilitiesEarly) -  Identify the sticky capability, deconstruct it into well defined domain concepts and then [reify](https://en.wikipedia.org/wiki/Reification_(computer_science)) those domain concepts into separate services.  
    ![Alt text](/images/stickysession.jpg)  