# REST & SOAP
* [REST Maturity Model](https://martinfowler.com/articles/richardsonMaturityModel.html) - Richardson Maturity Model (RMM) breaks down the principal elements of a REST approach into three steps. These introduce resources, http verbs, and hypermedia controls (HATEOAS - Hypertext As The Engine Of Application State)
    * Level 0 - Simply calling a remote service over URL 
    * Level 1 - Introduce resources
    * Level 2 - Introduce operations
    * Level 3 - Provide the URI for the next set of associated resources in the body of the response
* [REST vs SOAP](https://www.upwork.com/hiring/development/soap-vs-rest-comparing-two-apis/) - Comparing SOAP and REST is not really correct. REST API architectural style, light, fast, JSON, broadly accepted; SOAP - XML based, heavy, slower, xml schema, SOA architecture - [REST popularity](https://www.quora.com/Why-is-REST-becoming-more-popular-than-SOAP-these-days). 
SOAP is a protocol, and REST is an architectural style.

| SOAP      | REST |
| ----------- | ----------- |
| SOAP is a protocol i.e. set of rules that determine how data is transmitted between different devices in the same network      | REST is an architectural style i.e. high-level design guidelines and defers the implementation     |
| Heavier (xml tags) & hence requires more bandwidth    | Lighter (json) & hence requires less bandwidth        |
| It has WS-security (message based) on top of transport based security (SSL) | It relies on transport level security (SSL) |
| Supports XML format only | Allows JSON, XML, HTML, etc |

* [REST API - large binary files](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design#support-partial-responses-for-large-binary-resources)
* [REST API versioning](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design#versioning-a-restful-web-api) - URI versioning, Header versioning

* Application Programming Interface (API) - Allows communication between two systems 
* REST APIs are based on URIs (Uniform Resource Identifier, of which a URL is a specific type) and the HTTP protocol and use JSON for a data format, which is super browser-compatible. (It could also theoretically use the SOAP protocol) 
* SOAP is a protocol, and REST is an architectural style. A REST API can actually utilize the SOAP protocol, just like it can use HTTP.
* What is the difference between PUT, POST and PATCH? POST is always for creating a resource ( does not matter if it was duplicated ) PUT is for checking if resource is exists then update , else create new resource. PATCH is always for update a resource.
* What is difference between head and get? The HEAD method is identical to GET except that the server MUST NOT return a message-body in the response.
