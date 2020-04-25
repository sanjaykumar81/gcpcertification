# gcp certification

Contains my notes for GCP cloud certifications.

## Cloud computing

### us department of state

Cloud computing:  Cloud computing is a model for enabling convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.  Cloud computing promotes availability and is composed of five essential characteristics: on-demand self-service, broad network access, resource pooling, rapid elasticity, and measured service.  NIST SP 800-145 defines cloud computing as “a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service-provider interaction.”  For further guidance on cloud computing, see NIST Special Publication 800-145 -The NIST Definition of Cloud Computing

#### Key Points

- On demand self service - on demand provisioning of resource without human intervention
- Broad network access -- access from anywhere
- Resources pooling -- resources are shared by provide with multiple customer.
- Rapid elasticity -- easy to provision or release resources
- Measured service -- Pay for what you use.

## Zones and Regions

- Zone for fault tolerance
- Region for DR and getting closer to clients

## Pricing

- Billing for services billed by seconds of use
- Sustained use discount
- Discount for continues use
- Discount for using preemptible machines
- Can build custom machine to reduce pricing

## Security

Key thing to note from many things google does for security are

- Encryption at rest
- Encryption of inter-service communication

- Quotas

- Rate Quota
- Allocation Quota

## Principle of least privilege

- This principle says that each user should have only those privileges needed to do their jobs

## GCP resource hierarchy

- Organisation
- Folder
- Project
- resource

## Policies rules

- Policies are inherited downwards and are transitive
- More generous policy take precedence
- Resource policy is union of parent and resource policies

## who of google security

- a google account
- a google group
- a service account
- an entire g-suit
- or a cloud identity domain

## Roles in GCP

- Primitive (Owner, Editor, Viewer) -> applies to all gcp resources in a project
- Pre-defined -> are granular and apply to specific resource in a project
- Custom -> Can be created to using pre-defined role and can apply at org or project level and can't be applied at folder level.

## Service account -- for m/c to m/c communication

- can use to authenticate an app or machine
- service account authenticate using key. These key are managed by Google
- every vm can be associated with a service account

## Ways to interact with GCP

- Cloud console
- Cloud shell and sdk
- Cloud console mobile app
- Rest based api

## GCP VPC

- The Virtual Private Cloud networks that you define have global scope
- VPC can have subnets in any GCP region
- Subnet has regional scope
- Subnet can span across zones
- You can also have resources in different zones on the same subnet
- You can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it
- Doing that doesn't affect already configured VMs.

## Routes

- These are used to forward traffic from one instance to another instance within the same network.
- Even across sub-networks and even between GCP zones without requiring an external IP address.
- VPCs routing tables are built in, you don't have to provision or manage a router.
- Every VPC network uses a scalable, distributed virtual routing mechanism.

## Firewall

- Firewall rules control incoming or outgoing traffic to an instance
- By default, incoming traffic from outside your network is blocked
- Firewall rules can be based on tags

## Load Balancer

- HTTP(S) Load Balancing (Layer 7)
  - Options
    - Internet-facing or internal
    - Single- or multi-region
- TCP Load Balancing (Layer 4)
  - Options
    - Internet-facing or internal
    - Single- or multi-region
- UDP Load Balancing (Layer 4)
  - Options
    - Internet-facing or internal
    - Single-region

## VPN interconnect options

- VPN - Over internet
- Direct Peering - For more security and band width
- Carrier Peering - Where PoP is not available for Direct Peering. No SLA defined.
- Dedicated interconnect

## Cloud Bigtable  vs Cloud Datastore

### Bigtable

- Cloud Bigtable is Google's NoSQL, big data database service.
- Bigtable can `scale to billions of rows and thousands of columns`.
- Bigtable allowing you to `store petabytes` of data.
- GCP fully managed service.
- It's ideal for data that has a single lookup key. Some applications developers think of Bigtable as a persistent hatch table.
- Cloud Bigtable is ideal for storing large amounts of data with very low latency.
- `It supports high throughput, both read and write, so it's a great choice for both operational and analytical applications including Internet of Things, user analytics and financial data analysis.`
- Cloud Bigtable is offered through the same open source API as HBase, which is the native database for the Apache Hadoop project.
- Bigtable is actually the same database that powers many of Google's core services including search, analytics, maps and Gmail.
- Data can also be streamed in through a variety of popular stream processing frameworks, like Cloud Dataflow Streaming, Spark Streaming and Storm. 
- If streaming is not an option, data can also be read from and written to Cloud Bigtable through batch processes like Hadoop map reduce, Dataflow or Spark. Often summarized or newly calculated data is written back to Cloud Bigtable or to a downstream database.

### Datastore

- Highly scalable NoSQL database is Cloud Datastore.
- One of its main use cases is to `store structured data from App Engine apps.`
- You can also build solutions that span App Engine and Compute Engine with Cloud Datastore as the integration point.
- A fully-managed service.
- Cloud Datastore automatically handles sharding and replication, providing you with a highly available and durable database that scales automatically to handle load.
- Unlike Cloud Bigtable, it also `offers transactions` that affect multiple database rows.
- Support `SQL-like queries`.
- `Terabytes` of data
- `Free daily quota to use`

## Cloud SQL and Spanner

- Both are relational database
- Consistent and correctness
- Support transactions
- Fully managed service

## Cloud SQL

- It offers you your `choice of the MySQL or PostgreSQL`
- capable of handling `terabytes of storage`.
- on-demand or scheduled backups
- It can also scale both vertically by changing the machine type, and horizontally via read replicas. 

## Spanner

- It offers `transactional consistency at a global scale`
- replication for high availability.
- `petabytes of capacity`.
- Consider using Cloud Spanner if you have outgrown any relational database, or sharding your databases for throughput high performance, need transactional consistency, global data and strong consistency, or just want to consolidate your database.
- Natural use cases include, financial applications, and inventory applications.

## Storage options use case

- Cloud Datastore is the best for semi-structured application data that is used in app engines' applications.
- Bigtable is best for analytical data with heavy read/write events like AdTech, Financial or IoT data.
- Cloud Storage is best for structured and unstructured, binary or object data like images, large media files and backups.
- SQL is best for web frameworks and in existing applications like storing user credentials and customer orders.
- Cloud Spanner is best for large scale database applications that are larger than two terabytes; for example, for financial trading and e-commerce use cases.

## GKE

- Uses compute engine for its cluster resources.

## App Engine

- App Engine is `managed service`, a PaaS offering.
- Manages the hardware and networking infrastructure required to run your app.
- App Engine provides you with a `built-in services` that many web applications need. `NoSQL databases, in-memory caching, load balancing, health checks, logging and a way to authenticate users`. 
- You code your application to take advantage of these services and App Engine provides them. 
- `Automatic scaling` based on load
- Suited for applications where the workload is highly variable or unpredictable like web applications and mobile backend. 

### Standard vs Fleible

- App Engine offers two environments: standard and flexible.

### Sandard

- `Free daily usage quota`. 
- Standard SDK allow to deploy application using cli.
- Supports specific versions of Java, Python, PHP and Go.
- App Engine standard run  your code in a so-called "Sandbox.
- Like all Sandboxes, it imposes some constraints. For example, your application can't write to the local file system. It'll have to write to a database service instead if it needs to make data persistent.
- All the requests your application receives has a 60-second timeout,
- Can't install arbitrary third party software.

### Flexible

- No Free daily usage quota
- Run your app as containers and not in a sandbox
- Uses Compute Engine as VMs to run these containers.
- App Engine manages these Compute Engine machines for you. `You can choose which region these compute engine runs.`
- Application can still use  App Engine services such as data store, memcached, task queues, and so on. 
- Standard environment starts up instances of your application faster, but that you get less access to the infrastructure in which your application runs.

|  Standard      |Flexible        |
|----------------|----------------|
|Fast startup(millis)    | Slow startup (minutes)  |
|No SSH access   |  Can SSH       |
|No 3rd party s/w   | Yes can have 3rd party software |

## API management tools

### Cloud Endpoints

- Used when your service is running in GCP.
- So share your api with other developers you trust.
- Help monitor API use.
- To identify who is making the call
- API console for easy management of APIs.

### Apigee Edge

- Focus on business problems like rate limiting, quotas, and analytics.
- Suitable when actual service is running outside of GCP platform.
- Instead of replacing a monolithic application in one risky move, they can instead use Apigee Edge to peel off its services one by one, standing up microservices to implement each in turn, until the legacy application can be finally retired.

## Stackdriver

- Stackdriver is GCP's Solution for monitoring, logging and diagnostics requirement.
- Stackdriver gives you access to many different kinds of signals from your infrastructure platforms, virtual machines, containers, middleware and application tier, logs, metrics and traces. 
- Gives you insight into your application's health, performance and availability.
- Core components of Stackdriver: Monitoring, Logging, Trace, Error Reporting and Debugging.
- You can configure uptime checks associated with URLs, groups or resources such as Instances and load balancers.
- You can set up alerts on interesting criteria, like when health check results or uptimes fall into levels that need action.
- You can use Monitoring with a lot of popular notification tools.
- Create dashboards to help you visualize the state of your application.
- Stackdriver Logging lets you view logs from your applications and filter and search on them.
- Logging also lets you define metrics, based on log contents that are incorporated into dashboards and alerts.
- You can also export logs to BigQuery, Cloud Storage and Cloud PubSub. Stackdriver 
- Error Reporting tracks and groups the errors in your cloud applications. And it notifies you when new errors are detected. 
- With Stackdriver Trace, you can sample the latency of app engine applications and report Per-URL statistics.
- Stackdriver Debugger connects your applications production data to your source code. You can inspect the state of your application at any code location in production. 
- That means you can view the application stage without adding logging statements. Stackdriver Debugger works best when your application source code is available, such as in Cloud Source repositories. Although it can be in other repositories too.

## Google Cloud Big Data Solutions

- Dataproc -- adohoc hadoop clusters 
- DataProc - steam or batch processing
- BigQuery - datawarehouse

### This to learn
- lOad balancer
- vpns

### routing tables

- These are used to forward traffic from one instance to another instance within the same network.
- Even across sub-networks and even between GCP zones without requiring an external IP address.
- VPCs routing tables are built in, you don't have to provision or manage a router.

### firewall instance

- VPCs give you a global distributed firewall.
- You can control to restrict access to instances, both incoming and outgoing traffic.
- You can define firewall rules in terms of metadata tags on Compute Engine instances.

### VPC Peering

- When company has several GCP projects and the VPCs need to talk to each other. If you simply want to establish a peering relationship between two VPCs so that they can exchange traffic.

### Shared VPC

- For full power of IAM to control who and what in one project can interact with a VPC in another.

## Cloud load Balancer

- Cloud Load Balancing is a fully distributed, software-defined managed service for all your traffic.
- Software defined so you don't have to worry about scaling or managing them.
- You can put Cloud Load Balancing in front of all your traffic - HTTP and HTTPS, other TCP and SSL traffic, and UDP traffic too.
- With Cloud Load Balancing, a single anycast IP frontends all your backend instances in regions around the world.
- Provides cross-region load balancing, including automatic multi-region failover.
- Cloud Load Balancing reacts quickly to changes in users, traffic, backend health, network conditions, and other related conditions.

### HTTPS load balancing

They're intended for traffic coming into the Google network from the internet.

- If you need cross regional load balancing for a web application, use HTTPS load balancing.
- For Secure Sockets Layer traffic that is not HTTP, use the global SSL proxy load balancer.
- If it's other TCP traffic that does not use Secure Sockets Layer, use the global TCP proxy load balancer.
- Those two proxy services only work for specific port numbers, and they only work for TCP.
- If you want to load balance UDP traffic or traffic on any port number, you can still load balance across a GCP region with the regional load balancer.
- Finally, what all those services have in common is that they're intended for traffic coming into the Google network from the internet.

### Internal load balancer

- To load balance traffic inside your project, between the presentation layer and the business logic layer of your application.
- It accepts traffic on a GCP internal IP address and load balances it across Compute Engine VMs.

### Google Cloud CDN

- Your customers will experience lower network latency.
- The origins of your content will experience reduced load and you can save money too.
- Once you've set up HTTPS load balancing, simply enable Cloud CDN with a single checkbox.
- CDN interconnect partner program allow you to use your existing  CDN providers.

### GCP and On prem connect

#### Virtual Private Network over internet

- Many customers start with a Virtual Private Network connection over the internet using the IPSEC protocol.
- To make that dynamic, they use a GCP feature called Cloud Router. Cloud Router lets your other networks and your Google VPC exchange route information over the VPN using the Border Gateway Protocol. For instance, if you add a new subnet to your Google VPC, your on-premises network will automatically get routes to it.

#### Direct Peering

- But some customers don't want to use the internet, either because of security concerns or because they need more reliable bandwidth.
- They can consider peering with Google using Direct Peering. 
- Peering means putting a router in the same public data center as a Google point of presence and exchanging traffic.
- Google has more than 100 points of presence around the world.

#### carrier peering

- Customers who aren't already in a point of presence can contract with a partner in the carrier peering program to get connected.
- One downside of peering though is that it isn't covered by a Google service level agreement.

#### interconnection

- Customers who want the highest uptimes for their interconnection with Google should use Dedicated Interconnect, in which customers get one or more direct private connections to Google.
- If these connections have topologies that meet Google's specifications, they can be covered by up to a 99.99 percent SLA.
- These connections can be backed up by a VPN for even greater reliability.

## Tables

- External 

|VPN | Direct peering| carrier peering| interconnnect |
|----|----|----|----|
|internet| POP and internet | internet and alternative of PoP | direct private connections to google| 
|low uptime|moderate uptimes|moderate uptimes|highest uptimes|
|low reliability|moderate reliability|moderate reliability| high reliability|
| NO SLA | No SLA | No SLA| SLA|

- Internal 

| VPC |  VPC peering|  Shared VPC|
|----|----|----|
|For a project | communication between  projects VPCs | Control over who does what using IAM