# Security

## ACL Essentials

* ACLs Operate at the network/subnet level.
* They support **allow AND deny** rules for traffic traveling into or out of a subnet.
* They are **stateless**: so return traffic must be allowed through an **outbound rule**.
* They process rules in number order when deciding whether to allow traffic.
* Rules are evaluated in order, staring with the lowest rule number.
* The last rule in every ACL is a "catch all" deny rule.
* A network access control list \(NACL\) is an **optional layer of security** for your VPC that acts as a **firewall** for controlling traffic in and out of one or more **subnets**.
* **Best practice** to increment numbers by 10 so if you have to place in a rule in a certain order it does not create an issue.

### ACL Rules

* Rules are evaluated from **lowest to highest based on "rule \#"**.
* The first rule found that applies to the traffic type is immediately applied, regardless of any rules that come after it.
* A subnet can only be associated with ONE NACL at a time.
* An NACL allows or denies traffic from entering a subnet. Once inside the subnet, other AWS resources my have an additional layer of security \(security groups\)

## Security Groups

* Security groups are very similar to NACLs in that they **allow/deny traffic**.
* However, security groups are security for the instance level.
* In addition, the way allow/deny "rules" work are different from ACLs:
  * Security groups support **only allow** rules.
  * They are **stateful** so return traffic requests are allowed regardless of rules.
  * **All rules** are evaluated before deciding to allow traffic.

**Best practice** is to allow ONLY traffic that is required.

## Bastion Host 

* A Bastion host is an EC2 instance that lives in a public subnet, and is used as a "gateway" for traffic that is destined for instances that live in private subnets.
* This means that we can use a bastion host as a "portal" to access EC2 instances that are located in a private subnet.
* It is considered the "critical strong point" of the network - as all traffic must pass through it first.
* It should have increased and extremely tight security \(usually with extra 3rd party security and monitoring software installed\).
* It can be used as an access point to "ssh" into an internal network \(to access private resources\) without a VPN.

## NAT Gateway

* A NAT Gateway is designed to provide EC2 instances that live in a private subnet with a route to the internet \(to download or update software\).
* It will prevent any hosts located outside of the VPC from initiating a connection with instances that are associated with it.
* It will only allowing incoming traffic through if a request for it originated form an instance in a private subnet.
* It is needed because instances launched into private subnets can't communicate with the open internet.
* Placing instances in a private subnet creates a higher level of security, but also creates the limitation of the instances not being able to download/ update software

#### A NAT Gateway MUST:

* Be created in a public subnet.
* Be part of the private subnets route table.

#### NAT instance

* A NAT instance is identical to a NAT gateway in its purpose.
* However, it is executed differently by configuring an actual EC2 instance to do the same job.
* A NAT instance is starting to become more of a legacy feature in AWS.

