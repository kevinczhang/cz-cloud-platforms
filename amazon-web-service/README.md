# Amazon Web Service

## AWS Account & Services Layer

The Account & Services Layer represents how you create, access, and manage an AWS account and it's services. From how you interact with an AWS account and managing user rights, to how you access and use various AWS services and features.

This layer is all about account management & managing services.

### Root User:

The user created when you first create your AWS account is called the "root" user. It's credentials are the email address and password used when signing up for your AWS account. By default, the root user has FULL administrative rights and access to every part of the account.

Best Practices for Root User: You should not use the root user for daily work and AWS administration. You should create a second user that has admin rights and sign in as that user for daily work.

You should always protect your root account with MFA.

### AWS users

Create an IAM user for yourself as well, give that user administrative permissions, and use that IAM user for all your work. By creating individual IAM users for people accessing your account, you can give each IAM user a unique set of security credentials. You can also grant different permissions to each IAM user. If necessary, you can change or revoke an IAM user's permissions any time. \(If you give out your root user credentials, it can be difficult to revoke them, and it is impossible to restrict their permissions.\)

### Account connection tools

To access the services, you can use the AWS Management Console, the Command Line Interface, or Software Development Kits \(SDKs\).

### AWS Infrastructure Container:

This represents the boundaries of AWS. Everything inside is part of AWS's infrastructure, inducing all of it's physical networking components and services. Everything outside represents items that are external to AWS, that either connect to AWS or belong to your or your company \(i.e. on-premises servers, the open internet or your personal computer\).

## Physical and Networking layer

### AWS Physical & Networking Layer

The Physical & Networking Layer represents the global infrastructure of AWS in terms of where resources are physically located around the world and how data flows through the AWS network.

This layer is all about how AWS is organized, and how internal and external communication with AWS works.

### Edge Location:

An Edge Location is an AWS datacenter which does not contain AWS services. Instead, it is used to deliver content to parts of the world.

An example would be CloudFront which is a CDN: Cached items such as a PDF file can be cached on an edge location which reduces the amount of “space/time/latency” required for a request from that part of the world.

### AWS Regions:

AWS is made up of regions which are a grouping of independently separated data centers in a specific geographic regions known as “Availability zones”, which provide the foundation for **High Availability and Fault Tolerance**.

Availability of regions allows the architect to design applications to conform to specific laws and regulations for specific parts of the world. When viewing a region in the console you will only view resources in one region at a time but they will be across all AZs within that region.

Some AWS services work “globally” and not within a specific region. For example users created in IAM will work across regions

### Availability Zones:

Availability zones work together in a region to make up a collection of your AWS resources. Properly designed applications will utilize multiple availability zones for fault tolerance and failover. AZ’s \(as they are known\) have direct low latency connections between each AZ in a region but each AZ is isolated from other AZ’s to ensure fault tolerance. 

Physically located in each **Availability Zone** is where you will find **AWS Data Centers**. These Data Centers house the servers that run most AWS services and provide the hardware for **VPC Networking**.

## Shared Security Responsibility Model

AWS is responsible for portions of the cloud, and you as the customer have portions of the cloud that you are responsible for, thus creating shared security responsibility.

### Your Responsibility

* IAM 
* Multi-factor authentication
* Password/Key Rotation 
* Access Advisor 
* Trusted Advisor 
* Security Groups 
* Resource-Based Policies 
* Access Control Lists 
* VPC Port scanning is against the rules even on your own environment \(ask AWS if you want to do this\) 
* Operating system level patches

### AWS's Responsibility

* Physical server level and below 
* Physical Environment security and protection \(fire/power/climate/management\) 
* Storage device decommissioning according to industry standards 
* Personnel security 
* Network Device Security and ACLs 
* AWS API endpoints - SSL 
* DDOS protection 
* EC2 Instances and spoofing protection \(Ingress/Egress filtering\) 
* EC2 Instance hypervisor isolation: Instances on the same physical device are still independent

### Service Differences 

#### AWS Lambda: 

* Generally, operating system patches are your responsibility 
* AWS Lambda is a fully-managed service that lets AWS handle responsibility for the OS 

#### Other managed services

* Some AWS managed services take on additional responsibility for you 
* Evaluate those services independently

