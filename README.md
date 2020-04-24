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

