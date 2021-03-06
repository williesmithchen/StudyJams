# Virtual Machines in the Cloud

Compute Engine lets you run virtual machines on Google’s global infrastructure. This module covers how Compute Engine works, with a focus on Google virtual networking.

### Key Concepts

* Identify the purpose of and use cases for Google Compute Engine
* Summarize the various Google Cloud Platform networking and operational tools and services
* Build a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.
* Build a Compute Engine virtual machine using the gcloud command-line interface.

---
## Module Introduction

> [![](https://img.youtube.com/vi/Xrkvo23K3Bc/0.jpg)](https://youtu.be/Xrkvo23K3Bc)

---
## Virtual Private Cloud (VPC) Network

> [![](https://img.youtube.com/vi/vB87rvnKzOE/0.jpg)](https://youtu.be/vB87rvnKzOE)

* Virtual Private Cloud Networking
    * Each VPC network is contained in a GCP project
    * You can provision Cloud Platform resources, connect them to each other, and isolate them from one another
* Google CLoud VPC networks are global; subnets are regional
    * You can also have resources in different zones on the same subnet. 
    * You can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it.

### Practice Quiz: Virtual Private Cloud (VPC) Network

1. (T/F) In Google Cloud VPCs, subnets have regional scope.
    > Answer: True.
    > Explanation: That's correct. VPC subnets can span the zones that make up a region. This is beneficial because your solutions can incorporate fault tolerance without complicating your network topology.
2. (T/F) If you increase the size of a subnet in a custom VPC network, the IP addresses of virtual machines already on that subnet might be affected.
    > Answer: False.
    > Explanation: That's correct. You can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it. Doing that doesn’t affect already configured VMs.

---
## Compute Engine

> [![](https://img.youtube.com/vi/flYqss0k1TI/0.jpg)](https://youtu.be/flYqss0k1TI)

* Compute Engine offers managed virtual machines
    * No upfront investment
    * Fast and consistent performance
    * Create VMs with GCP Console or `gcloud`
    * Run images of Linux or Windows Server
    * Picks memory and CPU: use predefined types, or make a custom VM
    * Pick GPUs if you need them
    * Pick persistent disks: standard or SSD
    * Pick local SSD for scratch space too if you need it
    * Pick a boot image: Linux or Windows Server
    * Define a startup script if you like
    * Task disk snapshots as backups or as migration tools
* Compute Engine offers innovative pricing
    * Per-second billing, sustained use discounts
    * Preemptible instances
    * High throughput to storage at not extra cost
    * Custom machine types: Only pay for the hardware you need
* Scale up or scale out with Compute Engine
    * Use big VMs for memory- and compute-intensive applications
    * Use Autoscaling for resilient scalable applications

### Practice Quiz: Compute Engine

1. (T/F) You can create Compute Engine virtual machines from the command line.
    > Answer: True.
    > Explanation: Correct! It's advantageous to create virtual machines from a command line when you want their configurations to be scripted and repeatable. The gcloud command, provided by Google Cloud as part of the GCP SDK, can create virtual machines with parameters you specify.
2. What is the main reason customers choose Preemptible VMs?
    * a. To improve performance.
    * b. To reduce cost.
    > Answer: b.
    > Explanation: That's correct! The per-hour price of preemptible VMs incorporates a substantial discount.

---
## Important VPC Capabilities

> [![](https://img.youtube.com/vi/2APBfBj4F8A/0.jpg)](https://youtu.be/2APBfBj4F8A)

*  You control the topology of your VPC network
    * Use its route table of forward traffic within the network, even across subnets
        * Even across sub-networks and even between GCP zones without requiring an external IP address.
        * VPCs routing tables are built in, you don't have to provision or manage a router.
    * Use its firewall to control what network traffic is allowed
    * Use Shared VPC to share a netwrok or individual subnets, with other GCP projects
        * VPCs belong to GCP projects
    * Use VPC Peering to interconnect networks in GCP projects
* With global Cloud Load Balancing, your application presents a single front-end to the world
    * Users get a single, global anycast IP address
    * Traffic goes over the Google backbone from the closest point-of-presence to the users.
    * Backends are selected based on load
    * Only healthy backends receive traffic
    * No pre-warming is required
* Google VPC offers a suite of load-balancing options
    | Global HTTP(S) | Global Proxy | Global TCP Proxy | Regional | Regional internal |
    |---|---|---|---|---|
    | Layer 7 load balancing based on load | Layer 4 load balancing of non-HTTPS SSL traffic based on load | Layer 4 load balancing of non-SSL TCP traffic | Load balancing of any traffic (TCP, UDP) | Load balancing of traffic inside a VPC |
    | Can route different URLs to different back ends | Supported on specific port numbers | Supported on specific port numbers | Supported on any port number | Use for the internal tiers of multi-tier applications |
* Cloud DNS is highly available and scalable
    * Create managed zones, then add, edit, delete DNS records
    * Programmatically manage zones and records using RESRful API or command-line interface
* Cloud CDN (Content Delivery Network)
    * Use Google's globally distributed edge caches to cache content close to your users
    * Or use CDN Interconnect if you'd prefer to use a different CDN
* Google Cloud Platform offers many interconnect options
    * VPN: Secure multi-Gbps connection over VPN tunnels
    * Direct Peering: Private connection between you and Google for your hybrid cloud workloads
    * Carrier Peering: Connection thriugh the largest partner of service providers
    * Dedicated Interconnection: Connect N X 10G transport circuits for private cloud traffic to Google Cloud at Google POPs
 
---
## Lab 2: Getting Started with Compute Engine

> [![](https://img.youtube.com/vi/1KMu0Z3XdXw/0.jpg)](https://youtu.be/1KMu0Z3XdXw)

* Please follow the details in [here](./Lab-2.md)

---
## Quiz: Google Compute Engine and Networking

1. (T/F) Google Cloud Load Balancing allows you to balance HTTP-based traffic across multiple Compute Engine regions.
    > Answer: True.
    > Explanation: Correct! With global Cloud Load Balancing, your application presents a single front-end to the world.
2. Which statement is true about Google VPC networks and subnets?
    * a. Networks are global; subnets are zonal
    * b. Networks and subnets are global
    * c. Networks are global; subnets are regional
    * d. Networks are regional; subnets are zonal
    > Answer: c.
3. An application running in a Compute Engine virtual machine needs high-performance scratch space. Which type of storage meets this need?
    * a. Local standard
    * b. SSD persistent
    * c. Standard persistent
    * d. Local SSD
    > Answer: d.
4. Choose an application that would be suitable for running in a Preemptible VM.
    * a. A batch job that cannot be checkpointed and restarted
    * b. A batch job that can be checkpointed and restarted
    * c. An online relational database
    * d. An interactive website
    > Answer: b.
5. How do Compute Engine customers choose between big VMs and many VMs?
    * a. Use big VMs for in-memory databases and CPU-intensive analytics; use many VMs for fault tolerance and elasticity
    * b. Use big VMs for fault tolerance and elasticity; use many VMs for in-memory databases and CPU-intensive analytics
    > Answer: a.
6. How do VPC routers and firewalls work?
    * a. They are managed by Google as a built-in feature.
    * b. Customers provision virtual machines and run their routers and firewalls in them.
    * c. They are managed by Google in virtual machines, which customers may tune or turn off.
    * d. They are managed by Google in virtual machines, which customers may never modify.
    > Answer: a.
7. A GCP customer wants to load-balance traffic among the back-end VMs that form part of a multi-tier application. Which load-balancing option should this customer choose?
    * a. The global HTTP(S) load balancer
    * b. The global TCP proxy
    * c. The regional load balancer
    * d. The regional internal load balancer
    * e. The global SSL proxy
    > Answer: d.
8. For which of these interconnect options is a Service Level Agreement available?
    * a. Carrier Peering
    * b. VPNs with Cloud Router
    * c. Direct Peering
    * d. Dedicated Interconnect
    > Answer: d.

