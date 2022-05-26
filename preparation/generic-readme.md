# Generic - Technical interview questions & answers
1. Describe the actions when attempting to contact a website from your browser - Once you enter the website address, first the browser will search if the IP corresponding the DNS name is cached or not. If not, the DNS server will return the corresponding IP address. Once the IP address is found, it will establish a TCP connection with the server. The browser will then send a HTTP request to the web server with all the headers. The server will then process the request & send back response in the respective format to the browser. The browser will then display the response. For next requests, the static content like images, stylesheets will be cached by the browser, so it doesn't have to fetch them again. [Detailed explanation](https://medium.com/@maneesha.wijesinghe1/what-happens-when-you-type-an-url-in-the-browser-and-press-enter-bb0aa2449c1a)
2. Design a reservation system - [Video explanation](https://www.youtube.com/watch?v=6wSk5XG4jwU)
3. 32 bit vs 64 bit - [Video explanation](https://www.youtube.com/watch?v=Wu2A4fpFzgs)

* What is Three-Tier Architecture? Physical computing tiers: the presentation tier, or user interface; the application tier, where data is processed; and the data tier, where the data associated with the application is stored.

* What is three layer architecture? Logical layers are merely a way of organizing your code. You can have all the three layers in same physical tier.

* What is Pub-Sub? Any message published to a topic is immediately received by all of the subscribers to the topic. E.g. people subscribe to news, stock updates, will receive a message whenever there is an update from the publisher. A message filtering policy can be set by the subscriber based on Topic or Message attributes. It is a <ins>asynchronous</ins> service-to-service communication, used to enable <ins>Event driven architecture</ins>. Publish-subscribe model are implemented via a message broker. [Pub-Sub messaging basics](https://aws.amazon.com/pub-sub-messaging/)

* What is MQ? Messages are stored on the queue until they are processed and deleted. Each message is processed only once, by a single consumer. E.g. emails for marketing campaigns. It is a <ins>asynchronous</ins> service-to-service communication, used to enable <ins>Event driven architecture</ins>. MQs are implemented via a message broker. [MQ basics](https://aws.amazon.com/message-queue/)

* What is RTO & RPO? Recovery Time Objective (RTO) is the maximum acceptable delay between the interruption of service and restoration of service. This determines what is considered an acceptable time window when service is unavailable. Recovery Point Objective (RPO) Defined by the organization. RPO is the maximum acceptable amount of time since the last data recovery point. This determines what is considered an acceptable loss of data between the last recovery point and the interruption of service.RPO is used for determining the frequency of data backup to recover the needed data in case of a disaster.

* what's a hot standby? See below table. Hot Standby is used by organizations for testing their system failover. 

| High availability model | Secondary node behavior | Data protection | Failover time |
| ----------------------- | ----------------------- | --------------- | ------------- |
| Load-balanced (Active / Active)	| Both the primary node and the secondary node are active and they process system requests in parallel.	| Data replication is bidirectional and is performed based on the software capabilities.	| Zero failover time |
| Hot standby	| The software component is installed and available on both the primary node and the secondary node. The secondary system is up and running, but it does not process data until the primary node fails.	| Data is replicated and both systems contain identical data. Data replication is performed based on the software capabilities.	| A few seconds |
| Warm standby	| The software component is installed and available on the secondary server, which is up and running. If a failure occurs on the primary node, the software components are started on the secondary node. This process is automated by using a cluster manager.	| Data is regularly replicated to the secondary system or stored on a shared disk.	| A few minutes |
| Cold standby	| A secondary node acts as the backup for an identical primary system. The secondary node is installed and configured only when the primary node breaks down for the first time. Later, in the event of a primary node failure, the secondary node is powered on and the data is restored while the failed component is restarted.	| Data from a primary system can be backed up on a storage system and restored on a secondary system when it is required. |	A few hours |

* Describe failover - Failover is automatic switching to a redundant or standby computer server, system, hardware component or network upon the failure or abnormal termination of the previously active application, server, system, hardware component, or network in a computer network. Failover and switchover are essentially the same operation, except that failover is automatic and usually operates without warning, while switchover requires human intervention. [Wiki](https://en.wikipedia.org/wiki/Failover)

* What is a session? Establishing a communication channel between two network systems or between a user with an application.

* Caching is a high-speed data storage layer which stores a subset of data, typically transient in nature, so that future requests for that data are served up faster than is possible by accessing the data’s primary storage location. Caching allows you to efficiently reuse previously retrieved or computed data. [Caching - AWS](https://aws.amazon.com/caching/)

* What is encoding? Data transformation using algorithm. E.g. ASCII, BASE64. It is used for reducing the size of audio and video files. It can’t be used for securing data.

* What is Encryption? Process of encoding data using algorithm +  key or a password. E.g. AES encryption or RSA encryption. Encryption is for maintaining data <ins>**confidentiality**</ins>. Unencrypted data is called plain text; encrypted data is referred to as cipher text.
![alt text](/images/Encryption_vs_Encoding_vs_Hashing_1.png)

* What is Hashing? In hashing, data is converted to the hash using some hashing function, which can be any number generated from string or text. Various hashing algorithms are MD5, SHA256. Data once hashed is <ins>**non-reversible**</ins>.
![alt text](/images/hash-flow.png)
To integrate hashing in the password storage workflow, when the user is created, instead of storing the password in cleartext, we hash the password and store the username and hash pair in the database table. When the user logs in, we hash the password sent and compare it to the hash connected with the provided username. If the hashed password and the stored hash match, we have a valid login. It's important to note that we never store the cleartext password in the process, we hash it and then forget it. [Explanation](https://www.geeksforgeeks.org/encryption-encoding-hashing/)
![alt text](/images/Encryption_vs_Encoding_vs_Hashing_2.png)

* What is the difference between HTTP vs HTTPS? Hypertext Transfer Protocol Secure (HTTPS) - SSL/TLS secured transmission of data. TLS handshake establishes the secret keys with which they communicate. [TLS handshake explanation](https://github.com/abhinabsarkar/ssl-tls-handshake/blob/master/concepts/handshake-readme.md). Refer this link for the below mentioned questions as well
    * Explain difference between asymmetric and symmetric with some use cases
    * One way SSL vs two way SSL
    * SSL vs TLS
    * TLS is symmetric or asymmetric encryption

* What is a CDN? A content delivery network (CDN) is a group of geographically distributed servers that speed up the delivery of web content by bringing it closer to where users are. [CDN explained](https://www.akamai.com/our-thinking/cdn/what-is-a-cdn). CDNs cache content like web pages, images, and video from the origin servers to proxy servers near to your physical location also called <ins>**“points of presence” (PoPs)**</ins>. While a CDN does not host content and can’t replace the need for proper web hosting, it does help cache content at the network edge, which improves website performance. CDN server is like a reverse proxy server, which forwards the request to the origin web server & when the server returns the response for the first time, it will cache the files, images, video so that for all future requests from the clients in that region it will use the cached content to respond faster. 

* why you should use a CDN for a object with a zero TTL? If you set the TTL for a particular origin to 0, CDN will still cache the content from that origin (host server). It will then make a <ins>**GET request with an If-Modified-Since header**</ins>, thereby giving the origin a chance to signal that CDN can continue to use the cached content if it hasn't changed at the origin. 

    Using this saves bandwidth and reprocessing on both the server and client, as only the header data must be sent and received in comparison to the entirety of the page being re-processed by the server, then sent again using more bandwidth of the server and client. [Explanation - stackoverflow](https://stackoverflow.com/questions/10621099/what-is-a-ttl-0-in-cloudfront-useful-for)

* What is a routing table? It is a table that contains the routes to particular network destinations. It consists of network destination, next hop address (gateway) & local interface to reach destination. It also has metric which is used for making routing decision. The route will go in the direction of the gateway with the lowest metric.

    In the below example, 0.0.0.0 is the default route for any IP address which is not there in the routing table. The next hop is the gateway 10.0.0.1 & the local network interface is 10.0.0.4 from where the packet will be transmitted. [Routing table - wiki](https://en.wikipedia.org/wiki/Routing_table)

```cmd
C:\>route print
IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0         10.0.0.1         10.0.0.4     10
    168.63.129.16  255.255.255.255         10.0.0.1         10.0.0.4     11
```
* What is a datawarehouse? A transactional database doesn’t lend itself to analytics. To effectively perform analytics, you need a data warehouse. A data warehouse is a database of a different kind: an OLAP (online analytical processing) database. A data warehouse exists as a layer on top of another database or databases (usually OLTP databases). The data warehouse takes the data from all these databases and creates a layer optimized for and dedicated to analytics. Data Warehouse consumes data from various sources like multiple DBs, files, etc which is then analyzed using BI tools to make <ins>**data driven business decisions**</ins>. Data warehouses follow a <ins>**schema-on-write**</ins> approach (data is structured as it enters the warehouse). E.g. ChikfillA making decision based on the demand of chicken sandwich during specific hours. BI is mainly used for reporting or [descriptive analytics](http://www.dataversity.net/fundamentals-descriptive-analytics/). 

    ![alt text](/images/dwh.jpg)

    ![alt text](/images/business-intelligence-architecture-framework-diagram.png)

* What is a Data Mart? Data marts and data warehouses are both highly structured repositories where data is stored and managed until it is needed. However, they differ in the scope of data stored: data warehouses are built to serve as the central store of data for the entire business, whereas a data mart fulfills the request of a specific Line of Business (LOB).

* What is a datalake? Datalake is a centralized repository for structured & unstructured data (no schema). Data lakes commonly store sets of big data that can include a combination of structured, unstructured and semi-structured data. Data lakes follow a <ins>**schema-on-read**</ins> approach where data can be structured at query-time based on user needs. 
    * Datalake can be used by data scientists to make <ins>**Predictive Analytics**</ins>. E.g. 2016 U.S. election where Cambridge Analytica used data from facebook to come up with a predictive model to influence users.
    * Datalake can be used for Log analytics for growing volumes of event logs
    
    ![alt text](/images/datalake-architecture.png)

    In the above diagram, the different blocks of architecture are summarized below. [Explanation](https://www.iunera.com/kraken/fabric/data-lake/)
    1. Data Sources - data sources can range from structured data such as from a relational database or unstructured data such as from social media as well as Big Data. 
    2. Batch Data Processing - Frameworks including Kafka Streams, Spark streaming is used for processing the batch as well as the real time data
    3. Data Ingestion - Data is cleansed & standardized. [Explanation](http://users.cecs.anu.edu.au/~Peter.Christen/Febrl/febrl-0.3/febrldoc-0.3/node9.html) 
    4. Data Storage - store the mass different types of data (structured data, unstructured data, log files, real-time data, images, medical scans, social media and etc) to correlate many different data types. E.g. Hadoop & Cassandra.
    5. Data Analysis - data scientists and business analysts access data with their choice of analytic tools and frameworks.
    6. Reporting and Applications -  business intelligence (BI) tools such as Tableau help prepare data for analysis to build reports and dashboards. 

* What is SQl vs NOSQL?  
    SQL is a Relational DB which stores structured data with pre-defined schema & there is relationship between the tables using keys. SQL apply ACID properties to the transactions that guarantees data integrity:
    * Atomic - Transactions are all committed or rollback
    * Consistent - Transactions must follow the constraints or rules (like age < 25)
    * Isolation - transactions are isolated & are performed sequentially
    * Durable - transactions that have committed will persist into DB  

    SQL DB are mostly used in areas where accuracy, integrity & consistency are of utmost importance like OLTP. Online transaction processing (OLTP) captures, stores, and processes data from transactions in real time. SQL DBs are scaled <ins>**vertically**</ins>. (Sharding can be used to scale horizontally but it makes it complex & hard to maintain.)

    NOSQL stores unstructured (document, json) data with undefined schema & large data size. They are faster as there is no relationship defined & hence ideal for frequently changing data which has no fixed schema. It offers BASE features:
    * Basically Available - Mostly available
    * Soft-state - not guaranteed consistent
    * Eventually Consistent - It will be consistent over a period of time. 

    NOSQL is used when scale & availability are more important than consistency like OLAP. Online analytical processing (OLAP) uses complex queries to analyze aggregated historical data from OLTP systems. NOSQL DBs are scaled horizontally.
    
* How SQL & NoSQL databases are scaled? [Scaling databases in SQL & NoSQL](https://betterprogramming.pub/scaling-sql-nosql-databases-1121b24506df)
   * SQL DB - Vertical scaling
   * SQL DB horizontal sharding - difficult as you have to place a proxy service. Master slave with respect to replication
      
      ![alt text](/images/sql-horizontal-sharding.jpg)
      
   * NoSQL DB horizontal sharding - easier to scale as no master-slave concept rather all are nodes (equal). It follows a <ins>gossip protocol</ins> i.e. information is transferred from node to node
      
      ![alt text](/images/nosql-horizontal-sharding.jpg)

* CAP theorem states that any distributed data store which has partition, can guarantee either Consistency or Availability.
    * Consistency - All reads receive the most recent write or an error.
    * Availability - All reads contain data, but it might not be the most recent
    * Partition tolerance - The system continues to operate despite network failures.

* What is SSH? SSH provides a secure channel over an unsecured network by using a client–server architecture, connecting an SSH client application with an SSH server over port 22. 

* What is VPN? Virtual Private Network (VPN) extends private network across public network as if the computing devices are directly connected to the private network. VPN uses secure network protocol like IPSec or SSL/TLS that creates an encrypted secure tunnel between the systems which is sent over the public network (internet). 
![alt txt](/images/how-does-a-vpn-work-illustration.png)

* What is IPSec? It is a secure network protocol that creates an encrypted secure tunnel between two systems over internet.

* What is the difference between IPSec and SSL VPN? They both create secure tunnel over internet but the difference is IPSec operates at layer 3 whereas SSL at layer 4-7. 

    | Features  | IPSec VNP | SSL/TLS VPN |
    | - | --------- | ----------- |
    | Operates at |  Layer 3 | Layer 4 - 7 |
    | Protocol support | TCP 443 for TLS, UDP 500, 4500 for IKE/IPSec | TCP 443 for TLS |
    | Firewall | Can't go through firewall | Can go through firewall as TCP 443 only |
    | Connectivity | Connects remote host to entire network | Connect user to specific applications like email |
    | Example | Point to Site VPN, Site to Site VPN | Point to Site VPN |

    ![alt txt](/images/IPSecVPN-SSLVPN.png)
    * Protocols supported by P2S - [Explanation - Point to Site VPN Azure](https://docs.microsoft.com/en-us/azure/vpn-gateway/point-to-site-about#protocol)

* Reverse proxy - takes requests from the Internet and forwards these requests to one of the back-end web servers. The proxy server will terminate the incoming connection & then create a new connection. E.g. APIConnect solution implemented in UPS for external facing apps. Refer [link for explanation](https://github.com/abhinabsarkar/proxy-svc-endpoint)

* Forward Proxy - takes requests on behalf of the user & pass the received data. The proxy server will terminate the incoming connection & then create a new connection.  E.g.Proxy server on-prem. Refer [link for explanation](https://github.com/abhinabsarkar/proxy-svc-endpoint)

* What is MPLS? MPLS (Multiprotocol Label Switching) - uses labels to route packets instead of using IP addresses. It is a private connection linking data centers and branch offices. MPLS is typically outsourced, managed by service providers who guarantee network performance, quality and availability. Because MPLS is essentially a private network, it is considered reliable and secure, but also expensive.

    ![alt txt](/images/mpls.png)

* What is NAT?  NAT stands for network address translation. It's a way to map multiple local private addresses to a public one before transferring the information. Organizations that want multiple devices to employ a single IP address use NAT, as do most home routers.

    ![alt txt](/images/NAT_Concept-en.png)

* What is PAT? With Port Address Translation (PAT), a single public IP address is used for all internal private IP addresses, but a different port is assigned to each private IP address.

    ![alt txt](/images/pat_explanation.png)

* How would you limit downtime? What about maximizing uptime for the Db.

| Terminology | Definition | Image |
| ----------- | ---------- | ----- | 
| Availability Zone (AZ) | Availability zones are physically separate locations within each region that are tolerant to local failures i.e. redundant and separate power, networking, etc. Each zone consists of one or more data centers | ![alt txt](/images/regions-availability-zones.png)
| Region | region features datacenters deployed within a latency-defined perimeter. They're connected through a dedicated regional low-latency network. |

What is Federated Identity? Federated identity is related to single sign-on (SSO), in which a user's single authentication ticket, or token, is trusted across multiple IT systems or even organizations.
![alt text](/images/federated-identity.png)

What is SAML? How it is different from OAuth?
* SAML is an acronym used to describe the Security Assertion Markup Language (SAML). It enables you to access multiple web applications using one set of login credentials. SAML is one way to implement single sign on (SSO), and indeed SSO is by far SAML's most common use case. SAML is an XML-based markup language for security assertions
* Open authorization (OAuth) is an authorization process. Use it to jump from one service to another without tapping in a new username and password. 
* Both applications can be used for web single sign on (SSO), but SAML tends to be specific to a user, while OAuth tends to be specific to an application. The two are not interchangeable, so instead of an outright comparison, we’ll discuss how they work together.

What is Oauth2.0? OAuth 2.0 is an authorization protocol that gives an API/user client limited access to user resources. 
* OAuth2.0 --> Access token (contains user claims)
    * Access tokens expire after a period of time
    * Can use refresh token

What is OpenIDConnect? OPenIDConnect is an authentication protocol built on top of OAuth2.0. 
* OpenIDConnect --> ID token (identify the user - contains user profile) + Access token (contains user claims)

What is Custom Resource in k8s? Built-in resources in k8s comprises of Pods, Deployments, ConfigMaps, Services, etc. 
* A resource is an endpoint in the API (in this case k8s API)
* A custom resource is an extension of the Kubernetes API that is not necessarily available in a default Kubernetes installation
* CustomResourceDefinition(CRD) - CRD object creates a new custom resource with a name and schema that you specify. The Kubernetes API serves and handles the storage of your custom resource. [Example CRD](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#create-a-customresourcedefinition) & [Example Custom Object](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#create-a-customresourcedefinition). MySQL CRD, Postgress CRD are used in k8s Operator framework.

What is Operator in Kubernetes? Kubernetes operator is an application-specific controller that extends the functionality of the Kubernetes API to create, configure, and manage instances of complex applications on behalf of a Kubernetes user.     An operator is used to automate operations which are complex or require domain-specific knowledge like building a mysql db cluster which requires replication, updates, etc. They consist of additional Custom Resource Definitions (CRDs) and a controller that runs within the cluster.
[Kubernetes operator - youtube video](https://www.youtube.com/watch?v=ha3LjlD6g7g)
* Stateless apps in K8s
* Stateful apps in K8s without operator
* Stateful apps in K8s with operator
* Summary
    * CRDs + Custom Control loop
* Operator Hubs & SDK

    ![alt text](/images/k8s-operator.png)

Explain requests & limits in k8s? Requests and limits are the mechanisms Kubernetes uses to control resources such as CPU and memory. 
* Requests are what the container is guaranteed to get.
* Limits make sure a container never goes above a certain value.
* Limits > Requests (Always, else k8s will error out & won't let the container run)
* Requests and limits are on per-container basis
* You can set quotas at the Container level and at the Namespace level
* If a container exceeds the resource limit, the pod will be terminated

    ![alt text](/images/k8s-quota.png)

Explain Horizontal pod Auto Scaling (HPA), Cluster Auto Scaler, Over provisioner?
* HorizontalPodAutoscaler automatically updates a workload in response to increased load i.e. deploy more Pods.
* Cluster Auto Scaler - increases or decreases the size of a Kubernetes cluster (by adding or removing nodes), based on the presence of pending pods and node utilization metrics
* Over-provisioning - run a bunch of pause pods in our cluster with the sole purpose of reserving space to trick the cluster-autoscaler into adding extra nodes prematurely. Since these pods have a lower priority than regular pods they will be evicted from the cluster as soon as resources become scarce. The pause pods will then go into pending state which in turn triggers the cluster-autoscaler to add capacity.
    * Why Over-Provisioning? When using the cluster-autoscaler in its default configuration you will have a somewhat slow and unpredictable scaling behaviour. Only when pods go into pending state, the cluster-autoscaler will react by adding a node. Since it can take several minutes for node to launch and be ready to run pods this is not an ideal situation if you are running services that are sensitive to such scaling delays. 

What is readiness probe in k8s? Health check to see if the app is ready to serve traffic. E.g. app warm up and start. Three types of probes: HTTP, Command, and TCP
![alt text](/images/kubernetes-probe-readiness6ktf.gif)

What is a liveness probe in k8s? Health check to see if the pod is live. E.g. a deadlock in the app which causes it to stop serving requests. A liveness probe failure causes the pod to restart. You need to make sure the probe doesn’t start until the app is ready. Otherwise, the app will constantly restart and never be ready. So you configure initialDelaySeconds.
![alt text](/images/kubernetes-probe-livenessae14.gif)

What is CICD? 
* Continuous integration is a DevOps software development practice where developers regularly merge their code changes into a central repository, after which automated builds and tests are run. Continuous integration most often refers to the build or integration stage of the software release. 
* Continuous delivery is a software development practice where code changes are automatically prepared for a release to production. It expands upon continuous integration by deploying all code changes to a testing environment and/or a production environment after the build stage.
* E.g. are Jenkins, Azure DevOps. Benefits are 
    * Increased developer productivity
    * Identify bugs faster
    * Faster delivery

    ![alt text](/images/cicd.png)

What tools have you used for infrastructure monitoring?
* Dynatrace
* AppDynamics
* Prometheus

What is DOS, DDOS? How would you mitigate a DOS? A denial-of-service (DoS) attack floods a server with traffic, making a website or resource unavailable. A distributed denial-of-service (DDoS) attack is a DoS attack that uses multiple computers or machines to flood a targeted resource. Both types of attacks overload a server or web application with the goal of interrupting services. Steps to mitigate DDoS attack:
* Attack Detection - Analyzing incoming traffic and determining whether or not it’s legitimate is the first step in keeping your service available and responsive. IP reputation, common attack patterns, etc assist in early detection
*  WAF provides mitigation against layer 7 attacks whereas Network Firewalls respond against layer 4 attacks. 
* Akamai's Kona Site Defender & Barracuda Firewall provides WAF & DDoS protection.

What is Web Application Firewall (WAF)? It helps protect your web applications or APIs against common web exploits & attack patterns, such as SQL injection or cross-site scripting.
* SQL Injection - Security vulnerability via SQL code for backend database manipulation
* Cross Site Scripting - Security vulnerability via malicious scripts are injected

What's a Web Application Firewall? How's it differ from a firewall?
| Web Application Firewall | Network Firewall |
| ------------------------ | ---------------- |
| Works at Layer 7 | Works at Layer 3 & 4 |
| Application layer i.e. HTTP | Network layer i.e. TCP |
| Protects against attacks like SQL injection, CSS | Secures network at DMZ, intranet zone |

How SSO works?
![alt text](/images/how_sso_works.jpeg)

What is Identity Management? Identity management (or identity and access management - IAM) is an identity security framework that works to authenticate and authorize user.
* Tools to implement IAM
    * MFA, SSO
    * RBACs / Fine-grained access control
    * Zero Trust policy - review the access control periodically

What is a CDN? How does a CDN make web sites faster? A CDN is a geographically distributed network of servers that serves content from an “origin” server by caching content close to end user.
* It caches static files like images, scripts.
* They can also deliver dynamic content via low latency connections (Cloud based CDNs are on same network as the origin server, hence low latency)

How do you secure a web site? [Good sample answer](https://youtu.be/8zsdpwvTxos?t=426)

Open Policy Agent (OPA) - It ensures that you can enforce the policy to make sure that the docker containers aren't run in privileged or as a root user.

Privileged vs Root user - docker container [difference](https://www.cloudsavvyit.com/5211/privileged-vs-root-in-docker-whats-the-difference/)
* Root user - Docker daemon runs as root on the host machine, so by default all containers also run as root. Although containers are isolated using namespaces, a malicious user can escalate the privileges of a container & compromise the whole cluster. Always recommended to run as a non-root user.
* Privileged container - is a special flag you can set at runtime specifically to allow a Docker container to break free from its namespaces and access the entire system directly. Always recommended to set the privileged flag as false.
* [Refer for a simple example](https://github.com/abhinabsarkar/root-vs-privileged-container)

How would you secure an app running on a container?
* Container image security - Qualys container security
    * Update - the images so that they have the latest patches against the vulnerabilities
    * Scan - the image so that any new vulnerability is identified
    * Sign - the image so that you know the image hasn't been tampered with
* Image Registry security
    * Private - keep it private
    * Monitor 
    * Host server is secure
* Container Runtime 
    * App Security
    * Monitor network
* Container Orchestrator 
    * Limit the privileges on the container & user
    * Monitor Pod communication
* Host OS
    * Slim OS like SE-Linux
    * Access control on the Host
    * Monitor

What is a DNS based load balancer? DNS-based load balancing is a specific type of load balancing that uses the DNS to distribute traffic across several servers.  It does this by providing different IP addresses in response to DNS queries. Load balancers can use various methods or rules for choosing which IP address to share in response to a DNS query. Many of the DNS-based load balancing approaches are dynamic, meaning that the load balancers consider server health and server response times when assigning requests.
* Round-Robin DNS - If there are five IP addresses in round-robin DNS, a DNS query would only return IP address #1 for every sixth request. 
* weighted algorithm - weights based on their capacity to handle traffic
* proximity-based algorithm - assign traffic to the server closest to the user

    ![Alt text](/images/azure-loadbalancers.png)

What is Hadoop? [Youtube video basic explained](https://www.youtube.com/watch?v=aReuLtY0YMI)
* Apache Hadoop is an open source framework that is used to efficiently store and process large datasets ranging in size from gigabytes to petabytes of data. Instead of using one large computer to store and process the data, Hadoop allows clustering multiple computers to analyze massive datasets in parallel more quickly. Main components of Hadoop:
    * Hadoop Distributed File System (HDFS) – A distributed file system that runs on standard or low-end hardware. HDFS provides better data throughput than traditional file systems, in addition to high fault tolerance (3 copies of data on each node) and native support of large datasets.
    * MapReduce – A framework that helps programs do the parallel computation on data. The map task takes input data and converts it into a dataset that can be computed in key value pairs. The output of the map task is consumed by reduce tasks to aggregate output and provide the desired result.
    * Yet Another Resource Negotiator (YARN) – Manages and monitors cluster nodes and resource usage. It schedules jobs and tasks.
    * Hadoop Common – Provides common Java libraries that can be used across all modules.
    
* Design video streaming system like youtube, Netflix - [Youtube video - Raj](https://www.youtube.com/watch?v=7hZXBrI2TjY)
    * HLS (HTTP Live Streaming) - [HLS - blog](https://www.wowza.com/blog/hls-streaming-protocol)

* How to manage user session in microservice architecture? [User Sessions in Microservices](https://hackernoon.com/doing-microservices-user-sessions-right-the-fundamentals-hj3z34nu)

* What are WebSocket? WebSocket is bidirectional, a full-duplex protocol that is used in the same scenario of client-server communication, unlike HTTP it starts from ws:// or wss://. It is a stateful protocol, which means the connection between client and server will keep alive until it is terminated by either party (client or server). after closing the connection by either of the client and server, the connection is terminated from both the end. 

    ![alt text](/images/WebSocket-Connection.png)

    Web socket be used: 
    * Real time application like trading sites
    * Chat applications

    **How websocket different from HTTP?** HTTP is unidirectional where the client sends the request and the server sends the response. HTTP is stateless protocol runs on the top of TCP which is a connection-oriented protocol it guarantees the delivery of data packet transfer using the three-way handshaking methods and re-transmit the lost packets. When a client sends HTTP request to the server, a TCP connection is open between the client and server and after getting the response the TCP connection gets terminated, each HTTP request open separate TCP connection to the server, for e.g. if client send 10 requests to the server the 10 separate TCP connection will be opened. and get closed after getting the response/fallback. 

    ![alt text](/images/HTTP-Connection.png)

* What is a VLAN (Virtual Local Area Network)? - VLAN divides one or more LAN into multiple network segments - it is network segmentation. E.g. an organization may have separate VLANs for testing vs production, or have separate VLANs for different departments. Limitation of 4096 VLANs in a single LAN.

* What is VxLAN (Virtual Extensible LAN)? It is an overlay of (virtual) network on top of the underlying (physical) network - network virtualization. E.g. VxLAN used in RedHat OpenShift Container Platform for k8s networking via OpenShift SDN which uses Open vSwitch. Refer [OpenShift SDN plug-ins](https://github.com/abhinabsarkar/ocp4.x/blob/master/architecture/ocp-sdn-network-readme.md#openshift-sdn-plug-ins) and [OpenShift network flow](https://github.com/abhinabsarkar/ocp4.x/blob/master/architecture/ocp-sdn-network-readme.md#openshift-network-traffic-flow) for details where the 3 different traffic is explained.
    * [Intra node Pod traffic](https://github.com/abhinabsarkar/ocp4.x/blob/master/architecture/ocp-sdn-network-readme.md#intra-node-pod-traffic) using the OVS bridge 0
    * [Inter node Pod traffic](https://github.com/abhinabsarkar/ocp4.x/blob/master/architecture/ocp-sdn-network-readme.md#inter-node-pod-traffic) using VxLAN
    * [Pod to external (ingress/egress) traffic](https://github.com/abhinabsarkar/ocp4.x/blob/master/architecture/ocp-sdn-network-readme.md#pod-to-external-egress-traffic) using NAT

    ![alt text](/images/network-devices-node.jpg)

* Explain Apache Kafka Architecture - Apache Kafka is a distributed data store optimized for ingesting and processing streaming data in real-time. Streaming data is data that is continuously generated by thousands of data sources, which typically send the data records in simultaneously. A streaming platform needs to handle this constant influx of data, and process the data sequentially and incrementally.
   * [Basic Kafka concepts explained in a video](https://www.youtube.com/watch?v=udnX21__SuU&ab_channel=LearningJournal)
      * Ingests millions of data / second. 
      * Data pipeline for streaming real-time data and batch data
      * Built for scale. Fault tolerant.
      * Producers send messages to Topic. Consumers subsribe to Toic.
      * The consumers PULL data from Kafka. 
      * For scaling, Topics are partitioned. 
      * Partitions are distributed across multiple servers in a Kafka cluster. Data is written on the disk.
      * Offset is a number which is automatically generated (starts from 0) and assigned to messages.
      * To uniquely identify a message, Topic Name + Partition number + Offset ID
      * Message order is guaranteed only within a <ins>single partition</ins>
      
      ![alt text](/images/anatomy-of-topic.jpg)
      
    * With an annual content budget worth $16 billion, decision-makers at Netflix use data on subscriber behavior, user content preferences, etc of greater than 200 million users to make content-related decisions. It processess more than 500 billion events per day including error logs, user viewing activities, UI activities. It uses Kafka to make recommendations real-time based on the users 
    * Kafka's architecture (illustrated with 3 partitions, 3 replicas and 5 brokers.). Producers and consumers query Zookeeper for partition metadata (i.e., on which broker a stream partition leader is stored). Producers append to the partition's leader (e.g., broker 1 is assigned partition 1 leader), while exclusively one consumer pulls records from it starting at a given offset, initially 0. Records are appended to the last segment of a partition with an offset being associated to each record. Each partition has 2 other copies (i.e., partition's followers) assigned to other brokers that are responsible to pull data from the partition's leader in order to remain in sync.
    ![alt text](/images/kafka-architecture.jpg)

* How EventHubs or Apache Kafka works? If you are writing logs to storage from multiple sources, use something like Azure Event Hub or Apache Kafka before dumping it into storage. For example, Azure Event Hub is a data streaming service that streamlines the data pipeline for the users. It receives and processes <ins>millions of events per second</ins> with high throughput and low latency. The basic definition for it is that it decouples multiple event-producers from event-receivers.

    ![alt text](/images/Azure-Event-Hubs.png)

    ![alt text](/images/Azure-Event-Hub-Architecture.png)

    Event Hub in Azure that offers multiple sender/receiver concept. It allows the “Senders” to pass a message with high throughput and streamlines it in the partitions which are available in the Event Hubs. It may have single or multiple consumer groups to receive those messages. [How Event Hub works?](https://www.serverless360.com/blog/what-is-azure-event-hub) Example where Event Hub is used
    * Logging and telemetry

What is Swagger / Open API Specification (OAS)? 
* Swagger is a framework for API documentation. It includes automated documentation, code generation, and test-case generation. [Wiki](https://en.wikipedia.org/wiki/Swagger_(software))
* The OpenAPI Specification, previously known as the Swagger Specification, is a specification for machine-readable interface files for describing, producing, consuming, and visualizing RESTful web services. [Wiki](https://en.wikipedia.org/wiki/OpenAPI_Specification) 

    ![alt text](/images/swagger-vs-postman.png)

What are protocol buffers (protobuf)? mechanism for <ins>serializing</ins> structured data. It is developed by Google & is used in grpc framework.
* What is Serialization? converting object into stream of bytes so that it can be stored (for example, in a file or memory) or transmitted (for example, over a computer network) and reconstructed later (possibly in a different computer environment).

What is grpc (Google Remote Procedure Call)? 
* grpc is an open source framework developed by Google. It allows to define Request & Response for Remote Procedure Calls. It is built on top of HTTP/2 & uses protocol buffer (protobuf).

What is HTTP/2?
https://dev.to/techschoolguru/http-2-the-secret-weapon-of-grpc-32dk

How grpc works?
[The complete gRPC course Series' Articles](https://dev.to/techschoolguru/series/7311)

How Hadoop works?

How Kafka works?

How streaming video works - youtube, netflix, etc?

What is HIPPA, PCI/DSS, SOX, HITECH, GDPR?

TCPView for Windows? [TCPView](https://docs.microsoft.com/en-us/sysinternals/downloads/tcpview)
* [TCP connection status](https://9oelm.github.io/2018-05-06--Listening,-Established,-Close_wait-and-Time_wait-in-netstat/)

What is Event drive architecture? Event is an action which will change the state like button click to pay the bill from my phone. This will give me a response that the event is processed which in turn will then go through a series of asynchronous processing steps notifying each system to make changes into the state before I receive an email after two days that the bill has been paid.
