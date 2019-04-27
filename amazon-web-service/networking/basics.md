# Basics

## Internet Gateway

An internet gateway serves two purposes: to provide a target in your VPC route tables for internet-routable traffic, and to perform network address translation \(NAT\) for instances that have been assigned public IPv4 addresses.

* A VPC component that allows communication between instances in your VPC and the internet.
* It is horizontally scaled, redundant and highly available.
* It imposes no availability risks or bandwidth constraints on your network traffic.
* Provides NAT translation for instances that have a public IP addresses assigned \(public IP to private IP\)

#### Internet gateways rules and details need to know:

* Only 1 IGW can be attached to a VPC at a time.
* An IGW cannot be detached from a VPC while there are active AWS resources in the VPC.
* An IGW must be attached to a VPC if the resource inside the VPC need to connect to resources via the open internet.

To enable access to or from the internet for instances in a VPC subnet, you must do the following:

* Attach an internet gateway to your VPC.
* Ensure that your subnet's route table points to the internet gateway.
* Ensure that instances in your subnet have a globally unique IP address \(public IPv4 address, Elastic IP address, or IPv6 address\).
* Ensure that your network access control and security group rules allow the relevant traffic to flow to and from your instance.

## Route Tables

A _route table_ contains a set of rules, called _routes_, that are used to determine where network traffic is directed.

A route table's rules are comprised of two main components:

* Destination: The CIDR block range of the target \(where the data is routed to\)
* Target: A name identifier of where the data is being routed to.

By default, all subnets traffic is allowed to each other available subnet within your VPC which is called the local route and you cannot modify the local route

Unlike an IGW, you can have multiple "active" route tables in a VPC.

You cannot delete a route table if it has "dependancies" \(associated subnets\)

**Best practice** is to leave the default route table and create a new route table when new routes are needed for specific subnets.

## Subnets

A VPC spans all the Availability Zones in the region. After creating a VPC, you can add one or more subnets in each Availability Zone. When you create a subnet, you specify the CIDR block for the subnet, which is a subset of the VPC CIDR block. Each subnet must reside entirely within one Availability Zone and cannot span zones.

* If a subnet's traffic is routed to an internet gateway, the subnet is known as a _public subnet_. 
* If a subnet doesn't have a route to the internet gateway, the subnet is known as a _private subnet_. 
  * It creates a higher level of security, but it creates a limitation of an instance not being able to download/update software.
  * This issue is solved by routing traffic through a NAT instance.
* If a subnet doesn't have a route to the internet gateway, but has its traffic routed to a virtual private gateway for a Site-to-Site VPN connection, the subnet is known as a _VPN-only subnet_. 
* Subnet MUST be associated with a route table.
* By default all subnets traffic is allowed to each other available subnet within via the local target in the route table.
* A subnet is located in one specific availability zone and does not span AZs.



