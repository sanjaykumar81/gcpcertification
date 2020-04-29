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
  - There are three types of service accounts, user-created or custom, built-in, and Google APIs service accounts.
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

## Cloud load Balancer

- Cloud Load Balancing is a fully distributed, software-defined managed service for all your traffic.
- Software defined so you don't have to worry about scaling or managing them.
- You can put Cloud Load Balancing in front of all your traffic - HTTP and HTTPS, other TCP and SSL traffic, and UDP traffic too.
- With Cloud Load Balancing, a single anycast IP frontends all your backend instances in regions around the world.
- Provides cross-region load balancing, including automatic multi-region failover.
- Cloud Load Balancing reacts quickly to changes in users, traffic, backend health, network conditions, and other related conditions.

### Load Balancer

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
- Stackdriver logs by default are only stored for a limited number of days, the number of days depends on the type of log. 
- Admin Activity audit logs are kept for 400 days which helps if you need to do forensics. 
- Data Access audit logs are kept for only 30 days.

## Google Cloud Big Data Solutions

- Dataproc - adhoc hadoop clusters
- DataProc - steam or batch processing
- BigQuery - data warehouse

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

## Ways to interact with GCP

- Cloud Console
- Cloud shell and Cloud SDK
- REST API
- Cloud Mobile App

## Cloud Shell

- Cloud Shell is a temporary Virtual Machine with five gigabytes of persistent disk storage

- Temporary Compute Engine VM
- Command-line access to the instance via a browser
- 5 GB of persistent disk storage ($HOME dir)
- Pre-installed Cloud SDK and other tools
- gcloud: for working with Google Compute Engine and many Google Cloud services
- gsutil: for working with Cloud Storage
- kubectl: for working with Google Container Engine and Kubernetes
- bq: for working with BigQuery
- Language support for Java, Go, Python, Node.js, PHP, and Ruby
- Web preview functionality
- Built-in authorization for access to resources and instances

Every time you close Cloud Shell and reopen it, a new VM is allocated, and the environment variable you just set disappears. 

## routes

Routes tell VM instances and the VPC network how to send traffic from an instance to a destination, either inside the network or outside Google Cloud. Each VPC network comes with some default routes to route traffic among its subnets and send traffic from eligible instances to the internet

## firewall rules

Each VPC network implements a distributed virtual firewall that you can configure. Firewall rules allow you to control which packets are allowed to travel to which destinations. Every VPC network has two implied firewall rules that block all incoming connections and allow all outgoing connections.

## Cloud NAT

The `Cloud NAT gateway implements outbound NAT, but not inbound NAT`. In other words, hosts outside of your VPC network can only respond to connections initiated by your instances; they cannot initiate their own, new connections to your instances via NAT.

## Identity-Aware Proxy (IAP)

In order to connect to your private instance using SSH, you need to open an appropriate port on the firewall.
- IAP connections come from a specific set of IP addresses (35.235.240.0/20). 

## Sole tenant node

- A sole-tenant node is a physical Compute Engine server that is dedicated to hosting VM instances only for your specific project.
- Use sole-tenant nodes to keep your instances physically separated from instances in other projects, or to group your instances together in the same host hardware.
- Suitable for compliance requirements like isolation of VM from other VMs. e.g  payment processing workload
- A sole-tenant node can have multiple VM instances, but they all belong to the same project.
- Can accommodate VM instances up to 96 V CPUs and 624 gigabytes of memory.

## Hardend /Shielded VM

- Shielded VMs `offer verifiable integrity of VM` instances. 
- Shielded VMs verifiable integrity is achieved through the use of secure boot, Virtual Trusted Platform Module or VTPM enabled measured boot and integrity monitoring.
- Providing verifiable integrity, and offering features like VTPM shielding or ceiling that `help prevent data exfiltration`
- In order to use the shielded VM features, you need to select a shielded image.

## IAM

- who
  - Google Accounts, Service Accounts, Google Groups, G Suite Domains, and Cloud Identity Domains
    - A Google Account represents a developer, an administrator or any other person who interacts with GCP
    - A Service Account is an account that belongs to your application
    - A Google Group is a named collection of Google Accounts and Service Accounts
    - Google Groups are a convenient way to apply an access policy to a collection of users.
    - G Suite Domains, represent your organization's Internet domain name, such as example.com
    - Cloud Identity, lets you manage users in groups using the Google Admin Console.
    - Using Google Cloud Directory Sync, your administrators can log in and manage GCP resources, using the same usernames and passwords they already use.  This tool synchronizes users and groups, from your existing Active Directory or LDAP system.
    -  GCP also provides Single Sign-On Authentication.

- what
- which

### Policy

- policy contains a set of roles, and role members.

### Service account

- A service account is an account that belongs to your application instead of to an individual end user.
- This provides an identity for carrying out server-to-server interactions in a project without supplying user credentials.
- By default, all projects come with the built-in Compute Engine default service account. 
-Apart from the `default service account`, all projects come with the Google Cloud Platform APIs service account.
- Service account email:  `project-number@cloudservices.gserviceaccount.com`
- Custom service accounts provide more flexibility than the default service account, but they require more management from you.
- You can create as many custom service accounts as you need, assign any arbitrary access scopes, or Cloud IAM roles to them, and assign the service accounts to any Virtual Machine instance.
- `Default Compute Engine service account`. Automatically created per project. Identifiable by the email : `project-number-compute@developer.gserviceaccount.com`, and it is automatically granted the editor role on a project. 
- Access scopes are actually the legacy method of specifying permissions for your VM. Before the existence of IAM roles, access scopes were the only mechanism for granting permissions to service accounts. 
- For user-created service accounts, use Cloud IAM roles instead to specify permissions. 
- Another distinction between service accounts is that `default service account support both primitive and predefined roles`. But `user-created service accounts only use predefined IAM roles`.
- Roles for service accounts can also be assigned to groups or users.
- You assign the service accounts to the VMs when they are created,
- service accounts are authenticated using keys.

## Cloud Firetore is next gen version of Cloud Datastore

- A `highly scalable NoSQL database` for your applications,
- It is a fast, fully managed, serverless Cloud native, NoSQL document database, for your mobile, web, and IoT apps at global scale.
- Provide live synchronization and offline support
- Cloud Firestore also `supports ACID transactions`.
- Provide `automatic multi-region replication and strong consistency`.
- `Cloud Firestore` is actually the `next generation of Cloud Datastore`.
- Cloud Firestore is backward compatible with Cloud Datastore, but the new data mode, real-time updates in mobile and web client library features are not. To access all of the new Cloud Firestore features, you must use `Cloud Firestore in native mode`.
- `A general guideline is to use Cloud Firestore in Datastore mode for new server projects and native mode for new mobile and web apps`.
- If your schema might change and you need an adaptable database, you need to scale to zero or you want low maintenance overhead scaling up to terabytes, consider using Cloud Firestore. Also, if you don't require transactional consistency, you might want to consider Cloud Bigtable.

## Lables and Tag

- Labels are a utility for organizing GCP resources.
- Labels are `key value pairs` that you can attach to your resources like `VMs, disks, snapshots, and images`.
- `Tags` are user-defined strings that are `applied to instances only` and are mainly `used for networking` such as applying `firewall rules`. 

## VPN

Cloud VPN securely connects your on-premise network to your GCP VPC network through an IPSec VPN tunnel.

- The IPSec VPN tunnels that Cloud VPN offers have a capacity of 1.5 to 3 Gbps per tunnel and require VPN device on your On-premise network. The 1.5 Gbps capacity applies to the traffic that traverses the public Internet and the three Gbps capacity applies to the traffic that is traversing a Direct Peering link.

### HA VPN

- HA VPN is a high-availability (HA) Cloud VPN solution that lets you securely connect your on-premises network to your Virtual Private Cloud network through an IPsec VPN connection in single region.
- HA VPN provides an SLA of 99.99% service availability
- Each of the HA VPN gateway interfaces supports multiple tunnels. You can also create multiple HA VPN gateways.

### Classic VPN

- In contrast, Classic VPN gateways have a single interface, a single external IP address, and support tunnels using dynamic (BGP) or static routing (route based or policy based).
- They provide an SLA of 99.9% service availability.

## Cloud Routers

- Google Cloud Router enables dynamic route updates between your Compute Engine VPN and your non-Google network. Cloud Router eliminates the need to configure static routes and automatically discovers network topology changes.

## Cloud Interconnect

Interconnect lets you establish `high bandwidth`, `low latency` connections between your Google Cloud VPC networks and your on-premises infrastructure.

### Direct Peering and Carrier Peering. 

These services are useful when you require access to Google and Google Cloud properties. Google allows you to establish a direct peering connection between your business network and Google's.

- `With this connection, you will be able to exchange internet traffic between your network and Google's at one of the Google's broad-reaching Edge network locations`.
-After a direct peering connection is in place, you can use it to reach all the Google's services including the full suite of Google Cloud Platform products.
- Unlike dedicated interconnect, direct peering does `not have an SLA`.
- In order to use direct peering, you need to satisfy the certain peering requirements.
- Now, just like direct peering, carrier peering also does not have an SLA. Let
- `Direct peering has a capacity of 10Gbps per link` and requires you to have a connection in a GCP Edge point of presence.
- Carrier peering's capacity and requirements vary depending on the service provider that you work with.

### Dedicated Interconnect

- Dedicated Interconnect provides direct physical connections between your on-premises network and Google’s network.
- Dedicated Interconnect enables you to transfer large amounts of data between networks, which can be more cost effective than purchasing additional bandwidth over the public Internet.
- A `single connection can be a single 10G link`, a single `100G link`, or a link bundle, connected to a single Cloud Router.
- `SLA bound`

###  Partner Interconnect

- Partner Interconnect provides connectivity between your on-premises network and your VPC network `through a supported service provider`. 
- A Partner Interconnect connection is useful if your data center is in a physical location that `can't reach a Dedicated Interconnect colocation facility` or if your data needs `don't warrant an entire 10 Gbps connection`


|            |Dedicated        | shared          | Use case | SLA bound| Speed| RFC 1918|
|------------|-----------------|-----------------|----------|----------|------|---------|
|Layer3      |Direct Peering   | Carrier Peering | High speed connectivity to reach all the Google's services including the full suite of Google Cloud Platform products| No| 10G| Access to Google public IPs only|
|Layer2      | Dedicated interconnect| Partner interconnect|Dedicated Interconnect enables you to transfer large amounts of data between networks| Yes| 10G or 100 G|direct access to RFC1918 IP addresses in your VPC with an SLA.|

## Loadbalancers

| Global| Http(s)| SSL Proxy| TCP proxy|
| ------|--------|----------|----------|
|Regional| Internal TCP/UDP (Anderomeda)| Network TCP/UDP (Maglev) | Internal Http(s)|

### HTTPS Load Balancer

- HTTPS Load Balancing which acts at layer seven of the OSI model.
- routing decisions based on the URL.
- `GCP HTTPS load balancing provides global load balancing for HTTPS requests destined for compute instances.`
- Uses `single any cast IP` address
- HTTPS load balancer handles `HTTP` and `HTTPS` traffic across multiple backend instances and across `multiple regions`.
- `HTTP requests are load balanced on port 80 or 8080, and HTTPS requests are load balanced on port 443.`
- Enables `content-based` and `cross-regional` load balancing.

### SSL Proxy and TCP proxy

- `SSL proxy` is a global load balancing service for encrypted, non-HTTP traffic.
- `TCP proxy` is a global load balancing service for unencrypted non-HTTP traffic.

### Network load balancer

- Network load balancing is a regional non proxied load balancing service.
- Traffic can only be balanced between virtual machine instances that are in the same region unlike a global load balancer.

### Internal load balancing

- Internal load balancing is a regional, private load balancing service for TCP and UDP based traffic.

## Big Query

- BigQuery is GCP's serverless, highly scalable, and cost effective Cloud data warehouse. It's a petabyte scale data warehouse that allows for super-fast queries using the processing power of Google's infrastructure. Because there's no infrastructure for you to manage, you can focus on uncovering meaningful insights using familiar SQL, without the need for the database administrator. BigQuery is used by all types of organizations, and there's a free usage tier to help you get started. For more information, see the links section of this video. You can access BigQuery by using the GCP console, by using the command line tool, or by making calls to the BigQuery REST API, using the variety of client libraries such as Java,.NET or Python. There are also several third-party tools that you can use to interact with BigQuery, such as visualizing the data, or loading the data. Here's an example of a query on the table with over 100 billion rows. This query processes over 4.1 terabyte, but takes less than a minute to execute. The same query would take hours if not days through a serial execution.

