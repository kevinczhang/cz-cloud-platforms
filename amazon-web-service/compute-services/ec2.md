---
description: >-
  Elastic Cloud Compute. As virtual servers in the cloud, EC2 instances are
  designed to mimic traditional on-premise servers in their design and
  operation.
---

# EC2

## Overview

* Amazon EC2 provides _**scalable virtual servers**_ in the cloud 
* An EC2 virtual server is known as an “**instance**” and can be made up of different **instance types and sizes** 
* The virtual servers can run different operating systems, but most commonly run a flavor of **Linux or Windows**

Instance Configuration: 

* EC2 instances are designed to mimic traditional on-premises servers, but with the ability to be commissioned and decommissioned on-demand for easy scalability and elasticity 
* EC2 instances are primarily comprised of the follow components: 
  * **Amazon Machine Image \(AMI\)**: The operating system and other settings 
  * **Instance Type**: The hardware compute power, RAM, network bandwidth, etc 
  * **Network interface**: public, private, or elastic IP addresses 
  * **Storage**: The instances "hard drive" 
    * Elastic Block Store \(EBS\) - which is "network persistent storage" 
    * Elastic File System \(EFS\) - "scalable, elastic file storage" 
    * Instance Store - which is "ephemeral storage"

### Other Important EC2 Facts: 

* A security group must be assigned to an instance during the creation process 
* Each instance must be placed into an existing VPC, availability zone, and subnet 
* Automated custom launch commands \(bootstrapping\) can be passed into the instance during launch via "user-data" scripts 
* "Tags" can be used to help name and organize provisioned instances 
* Encrypted key-pairs are used to manage login authentication 
* There are limits on the amount of instances you can have running in a region at any particular time

## Amazon Machine Images \(AMIs\):

A preconfigured package \(template\) required to launch an EC2 instance; includes an: Operating system, Software packages and Other required settings \(root storage type & virtualization type\).

Amazon Machine Images are used with Auto Scaling to quickly launch new servers on demand, and to quickly recover from disaster.

### AMIs come in three main categories:

* **Community AMIs**: Free to use Generally with these AMIs, you are just selecting the OS you want.
* **AWS Marketplace AMIs**: Pay to use Generally comes packaged with additional, licensed software. 
* **My AMIs**: AMIs that you create yourself.

## EC2 Instance Type:

* Instances Types describe the "hardware" components that an EC2 instance will run on: 
  * Compute power \(processor/vCPU\) 
  * Memory \(ram\) 
  * Storage Options/optimization \(hard drive\) 
  * Network Performance \(bandwidth\).
* Instance Types are grouped into families and types that you can choose from that have different purposes: 
  * General Purpose \(T2, M5, and M4\): 
    * T2 - Burstable performance, good for many general purposes 
    * M4/M5 - Small or mid-size databases, data processing, enterprise applications 
  * Compute Optimized - \(C4 and C5\): High performance web servers, science/engineering apps, ad serving 
  * Memory Optimized - \(X1e, X1, and R4\): High performance databases, in-memory databases, large data processing engines 
  * Accelerated Computing - \(P3, P2, G3, F1\): 
    * P2/P3 - Machine/Deep learning, high performance databases, server-size GPU compute workloads 
    * G3 - 3D visualizations and rendering, application streaming, video encoding, server-side graphics workloads 
    * F1 - Genomics research, financial analytics, big data, and security 
  * Storage Optimized - \(H1, I3, D2\):
    * D2/H1 - MapReduce, HDFS, network file systems, or data processing applications 
    * I3 - NoSQL databases \(Cassandra/MongoDB/Redis\), data warehouses, Elasticsearch

Learn more - [https://aws.amazon.com/ec2/instance-types/](https://aws.amazon.com/ec2/instance-types/)

## EC2 Purchasing Options:

#### On-Demand: 

* On-demand purchasing lets you choose any instance type and provision/terminate it at any time 
* Is the most expensive purchasing option 
* Is the most flexible purchasing option
* You are only charged when the instance is running \(and billed by the second\)

#### Reserved Instances \(RI\): 

* Reserved purchasing allows you to purchase an instance for a set time period of one or three years 
* This allows for a significant price discount over using on-demand 
* You can select to pay upfront, partial upfront, or none upfront 
* Once you buy a reserved instance, you own it for the selected time period and are responsible for the entire price - regardless of how often you use it 
* Purchases of AZ-specific RIs provide capacity reservation in that AZ. Regional RI purchases do not - so it is theoretically possible AWS will run out of capacity

#### Spot Instances: 

* Spot pricing is a way for you to "bid" on an instance type, and only pay for and use that instance when the spot price is equal to or below your "bid" price This option allows Amazon to sell the use of unused instances, for short amounts of time, at a substantial discount 
* Spot prices fluctuate based on supply and demand in the spot marketplace 
* You are charged per second \(with conditions\) 
* When you have an active bid, an instance is provisioned for you when the spot price is equal to or less than you bid price 
* A provisioned instances automatically terminate when the spot price is greater than your bid price. 
* Bid on unused EC2 instances for “non production applications”

#### Dedicated Hosts: 

A dedicated physical machine that you have full control over. This can help save money on license fees and meet certain regulatory compliances.

## EC2 Shared Responsibility Model:

The AWS shared responsibility model describes the responsibilities of both parties \(AWS & you\) for managing varying elements of AWS resources.

The customer \(you\) is responsible for managing the software level security on instances, including: 

* Security groups 
* Firewalls \(IP tables, Firewalld, etc\) 
* EBS encryption provided by AWS \(snapshots can also use EBS encryption\): 
  * AWS EBS encryption utilizes AWS Key Management Service 
  * Additional encryption methods include encrypting the entire file system using an encrypted file system 
* Applying an SSL Certificate to the ELB \(Elastic Load Balancer\)

AWS is responsible for managing the hypervisor and physical layer of security for EC2: 

* DDOS protection 
* Port scanning protection \(not allowed even in your own environment without permission from AWS\) 
* Ingress network filtering

## EC2 IP Addresses:

### Private IP Address: 

* All EC2 instances are automatically created with a PRIVATE IP address. 
* The private IP address is used for internal \(inside the VPC\) communication between instances

### Public IP Address: 

* When creating an EC2 instance, you have the option to enable \(or auto-assign\) a public IP address 
* A public IP address is required if you want the EC2 instance to have direct communication with resources across the open internet: i.e., If you want to directly SSH into the instance or have it directly serve web traffic 
* Auto-assigning is based on the setting for the selected subnet that you are provisioning the instance in

### Elastic IP Address \(EIP\): 

* An EIP is a static IPv4 address designed for dynamic cloud computing 
* An EIP is a public IPv4 address 
* With an EIP, you can attach a public IP address to an EC2 instance that was created with only a private IP address OR 
* You can mask the failure of an instance or software by rapidly remapping the address to another instance in your account \(i.e., detaching the EIP from one instance and attaching it to another\).
* Attaching an EIP to an instance will replace its default public IP address for as long as it is attached.

## Bootstrapping & User-Data/Meta-Data:

### Bootstrapping: 

* Refers to a self-starting process or set of commands without external input 
* With EC2, we can bootstrap the instance \(during the creation process\) with custom commands \(such as installing software packages, running updates, and configuring other various settings\)

```text
#!/bin/bash
yum update -y
yum install -y httpd
service httpd start
```

### User-Data: 

* A step/section during the EC2 instance creation process where you can include your own custom commands via a script \(i.e., a bash script\)
* Here is an example of a bash script that will automate the process of updating the yum package installer, install Apache Web Server, and start the Apache service:

### Viewing User-Data & Instance Meta-Data:

When logged into an EC2 instance, you can view the instance user-data used during creation, or meta-data by executing one of the the following commands: 

* curl [http://169.254.169.254/latest/user-data/](http://169.254.169.254/latest/user-data/) \(displays bootstrapping commands\) 
* curl [http://169.254.169.254/latest/meta-data](http://169.254.169.254/latest/meta-data) / \(displays AMI, instance type, etc.\)

## Storage options

### EC2 Elastic Block Store \(EBS\) Basics:

* EBS volumes are persistent, meaning that they can live beyond the life of the EC2 instance they are attached to 
* EBS backed volumes are network attached storage, meaning they can be attached/detached to or from various EC2 instances 
* However, they can only be attached to ONE EC2 instance at a time 
* EBS volumes have the benefit of being backed up into a snapshot - which can later be restored into a new EBS volume 
* By default, EBS volumes are replicated within the Availability Zone EBS volumes are usually mounted to the file system at /dev/sda1 or /dev/xvda

#### EBS Performance: 

* EBS volumes measure input/output operations in IOPS: 
  * IOPS are input/output operations per second 
  * AWS measures IOPS in 256KB chunks \(or smaller\) 
  * Operations that are greater than 256KB are separated into individual 256KB chunks 
  * For example, A 512KB operation would count as 2 IOPS 
* The type of EBS volume you specify greatly influences the I/O performance \(IOPS\) your device will receive 
* Even volumes with "**provisioned IOPS**" may not produce the performance you expect - If this is the case, an EBS optimized instance type is required, which prioritizes EBS traffic

#### Initializing EBS Volumes: 

* Volumes created from an EBS snapshot must be initialized 
* Initializing occurs the first time a storage block on the volume is read - and the performance impact can be impacted by up to 50% 
* You can avoid this impact in production environments by manually reading all the blocks

### EC2 Elastic Block Store Volumes:

#### General Purpose SSD: 

* Use for dev/test environments and smaller DB instances 
* Performance of 3 IOPS/GB of storage size \(burstable with baseline performance\) 
* Volume size of 1GB to 16TB 
* Considerations when using T2 instances with SSD root volumes \(burstable vs. baseline performance\)

#### Provisioned IOPS SSD: 

* Used for mission critical applications that require sustained IOPS performance 
* Large database workloads 
* Volume size of 4GB to 16TB 
* Performs at provisioned level and can provision up to 32,000 IOPS per volume

#### Throughput Optimized HDD and Cold HDD: 

* Cheaper than SSD options, also less performant 
* Cold HDD - Designed for less-frequent access 
* Volume size of 500GB - 16 TB 
* Cannot be a boot volume

#### EBS Magnetic \(Previous Generation\): 

* Low storage cost 
* Used for workloads where performance is not important or data is infrequently accessed 
* Volume size of Min 1GB Max 1 TB

### EC2 Instance Store Volumes:

* Instance-store volumes are virtual devices whose underlying hardware is physically attached to the host computer that is running the instance
* Instance store volumes are considered ephemeral data, meaning the data on the volumes only exists for the duration of the life of the instance
* Once the instance is “stopped” or “shutdown” the data is erased
* The instance can be rebooted and still maintain its ephemeral data
* Not all instance types can use instance store volumes

### EBS Snapshots:

Snapshots are point-in-time backups of EBS volumes that are stored in S3

#### Snapshot properties: 

* Snapshots are incremental in nature 
* A snapshot only stores the changes since the most recent snapshot, thus reducing costs \(by only having to pay for storage for the “incremental changes” between snapshots\) 
* However, if the "original" snapshot is deleted, all data is still available in all the other snapshots 
* Even though snapshot storage only charges you for the amount of incremental data in each snapshot, all prior data is still there 
* Snapshots can be used to create fully restored EBS volumes

#### A few other important snapshot notes: 

* Frequent snapshots of your data increases data durability - so highly recommended 
* When a snapshot is being taken against the EBS volume, it can degrade performance so snapshots should occur during non-production or non-peak load hours

## Elastic File System \(EFS\):

* EFS is a storage option for EC2 that allows for a scalable storage option 
* EFS storage capacity is elastic: 
  * The storage capacity will increase and decrease as you add or remove files 
  * Applications running on an EC2 instance using EFS will always have the storage they need, without having to provision and attach larger storage devices 
* EFS is fully-managed \(no maintenance required\) 
* Supports the Network File System version 4.0 and 4.1 \(NFSv4\) protocols when mounting 
* Best performance when using an EC2 AMI with Linux kernel 4.0 or newer

#### Benefits of EFS: 

* The EFS file system can be accessed by one \(or more\) EC2 instances at the same time: 
  * Shared file access across all your EC2 instances 
  * Applications that span multiple EC2 instances can access the same data 
* EFS file systems can be mounted to on-premises servers \(when connected to your VPC via AWS Direct Connect\): This allows you to migrate data from on-prem severs to EFS and/or use it as a backup solution 
* EFS can scale to petabytes in size, while maintaining low-latency and high levels of throughput 
* You only pay for the amount of storage you are using

#### Security: 

* Control file system access through POSIX permissions 
* VPC for network access control, and IAM for API access control 
* Encrypt data at rest using AWS Key Management Service \(KMS\)

When to use: Big Data and analytics Media processing workflows Web Serving & Content Management

## EC2 Key Pairs:

* EC2 key pairs are two cryptographically secure keys that are used by AWS to authenticate a client when logging into an EC2 instance 
* Each key pair consists of a public key and a private key 
* AWS stores the public key on the instance, and you are responsible for storing the private key

#### To log in to an EC2 instance, you must create and authenticate with a key pair:

* Linux instances have no password, and you use a key pair \(using SSH\) to log in 
* With Windows instances, you use a key pair to obtain the administrator password and then log in using RDP \(remote desktop protocol\) 
* During the creation process of an EC2 instance, you are required to either create a new key pair OR use an existing key pair - which will be tied to the instance 
* The private key is available for download and stored on your local device, however it is only available for download once in the form of a .pem file

#### To log in to Linux instances with SSH: 

* You will most likely need to change permissions on the .pem file before you can use it to log in via SSH 
* This is done by running the following command "chmod 400 \[key name\].pem"

## Elastic Load Balancer \(ELB\) Essentials:

* **Load balancing** \(as a concept\) is a common method used for distributing incoming traffic among servers 
* An **Elastic Load Balancer** is an EC2 service that automates the process of evenly distributing incoming traffic to all the instances that are assocaited with the ELB 
* An elastic load balancer can load balance traffic to multiple EC2 instances located across multiple availability zones 
* An ELB can help reduce compute power on an EC2 instance by allowing for an SSL certificate to be applied directly to the elastic load balancer

### Maintaining Session State with ELBs: 

* ELB Option 1 - Load Balancer Generated Cookie Stickiness: 
  * Load balancer will issue a cookie if the user doesn't have one 
  * Sends users to specific instance based on cookie 
* ELB Option 2 - Application Generated Cookie Stickiness: 
  * Load balancer will use an application-generated cookie to associate a session with an instance 
  * Sends users to specific instance based on the application-generated cookie 
* Non-ELB Option \(Recommended\) - Use a caching service such as Amazon ElastiCache: 
  * ELB Requests are evenly distributed to instances 
  * Instances then check ElastiCache \(using Redis or Memcached\) for the session 
  * If no session exists in ElastiCache the instance can check a backing database

