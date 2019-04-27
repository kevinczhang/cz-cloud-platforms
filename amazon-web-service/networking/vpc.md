# VPC

The basic VPC networking is to route data through AWS's networking infrastructure, identify services and features needed to properly route traffic including access points, external and internal traffic routing, security layers and instance endpoints.

Amazon Virtual Private Cloud \(Amazon VPC\) enables you to launch AWS resources into a virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.

VPC is designed to resemble:

* Private on-premise data centers
* Private corporate network

Private network features available in AWS VPCs:

* Private and public subnets
* Scalable architecture
* Ability to extend corporate/on-premise network to the cloud as if it was part of your network \(VPN\)

Important VPC Facts:

* A VPC is hosted within a chosen AWS region.
* A VPC spans multiple availability zones within a region.
  * This allows you to provision redundant resource in separate availability zones while having them accessible on the same network \(foundation of high availability and fault tolerant architecture\)
* AWS provides a DNS server for your VPC so each instance has a hostname. However, you can run your own DNS servers by changing the DHCP option set configuration within the VPC.

## Benefits

1. Ability to launch instances into a subnet.
2. Ability to define custom CIDR \(IP address range\) inside each subnet.
3. Ability to configure routes between subnets via route tables.
4. Ability to configure an internet gateway to provide a route to the internet for resources launched inside the VPC.
5. Ability to create a layered network of resources.
6. Ability to extend your on-premise network into the cloud with VPN/VPG and IPsec VPN tunnel.
7. Layered Security 
   1. Instance level security groups \(firewall on the instance level\)
   2. Subnet level network ACLs \(firewall on the subnet level\)

## Default VPC

* The default VPC is the VPC comes preconfigured in your AWS account when it is first created.
* It has different setup than a non-default VPCs.
* It is meant to allow the user easy access to a VPC without having to configure it from scratch.
* In the default VPC, all subnets have a route to the internet via route table and an attached IGW.
* Each instance launched in it has a private and public IP address \(defined on the subnet settings\).

## VPC Limits

* 5 VPCs per region \(more available upon request\)
* 5 internet gateways per region \(this is equal to your VPC limit because you can have one internet gateway attached to a VPC at a time\)
* 50 customer gateways per region.
* 50 VPN connections per region.
* 200 route tables per region / 50 entries per route table.
* 5 elastic IP addresses
* 500 security groups per VPC
* 50 rules per security group
* 5 security groups per network interface \(security groups although generally referred to as being on the on the instance level are technically on the VPC level\)



