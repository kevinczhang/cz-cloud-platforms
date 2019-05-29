# Virtual Private Clouds

A VPC network is a global resource which consists of a list of regional virtual subnetworks \(subnets\) in data centers, all connected by a global wide area network. VPC networks are logically isolated from each other in GCP.

![](../../../.gitbook/assets/image%20%2832%29.png)

## VPC networks have the following properties:

* VPC networks, including their associated routes and firewall rules, are [global](https://cloud.google.com/compute/docs/regions-zones/global-regional-zonal-resources) resources. They are _not_ associated with any particular region or zone.
* _Subnets_ are regional resources. Each subnet defines a range of IP addresses. For more information about networks and subnets, see [networks and subnets](https://cloud.google.com/vpc/docs/vpc#vpc_networks_and_subnets). Need to be unique within a VPC.
* Traffic to and from instances can be controlled with network [firewall rules](https://cloud.google.com/vpc/docs/vpc#firewall_rules).
* Resources within a VPC network can communicate with one another using internal \(private\) IPv4 addresses, subject to applicable network firewall rules with VPC routing. For more information, see [communication within the network](https://cloud.google.com/vpc/docs/vpc#intra_vpc_reqs).
* Instances with internal IP addresses can communicate with [Google APIs and services](https://developers.google.com/apis-explorer/). For more information, see [Private Access Options](https://cloud.google.com/vpc/docs/private-access-options).
* Network administration can be secured using [Identity and Access Management \(IAM\)](https://cloud.google.com/iam/docs/) roles.
* An [organization](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy#organizations) can use [Shared VPC](https://cloud.google.com/vpc/docs/shared-vpc) to keep a VPC network in a common host project. Authorized IAM members from other projects in the same organization can create resources that use subnets of the Shared VPC network.
* VPC networks can be connected to other VPC networks in different projects or organizations by using [VPC Network Peering](https://cloud.google.com/vpc/docs/vpc-peering).
* VPC networks can be securely connected in hybrid environments using [Cloud VPN](https://cloud.google.com/vpn/docs/concepts/overview) or [Cloud Interconnect](https://cloud.google.com/interconnect/docs/concepts/overview).
* VPC networks only support IPv4 [unicast](https://wikipedia.org/wiki/Unicast) traffic. They do **not** support [broadcast](https://wikipedia.org/wiki/Broadcasting_%28networking%29), [multicast](https://wikipedia.org/wiki/IP_multicast), or IPv6 traffic _within_ the network: VMs in the VPC network can only send to IPv4 destinations and only receive traffic from IPv4 sources. It is possible to create an IPv6 address for a [global load balancer](https://cloud.google.com/load-balancing/docs/ipv6), however.
* Flow logs capture information about the IP traffic going to and from network interfaces on Google Compute Engine. VPC flow logs help with network monitoring, forensics, real-time security analysis and expense optimization. GCP flow logs are updated every 5-seconds, providing immediate visibility.

#### Routes <a id="routes"></a>

Routes tell VM instances and the VPC network how to send traffic from an instance to a destination, either inside the network or outside of GCP. Each VPC network comes with some [system generated routes](https://cloud.google.com/vpc/docs/vpc#system-generated-routes) to route traffic among its subnets and send traffic from [eligible instances](https://cloud.google.com/vpc/docs/vpc#internet_access_reqs) to the Internet.

#### Forwarding rules <a id="forwarding_rules"></a>

While routes govern traffic leaving an instance, forwarding rules direct traffic _to_ a GCP resource in a VPC network based on IP address, protocol, and port.

Some forwarding rules direct traffic from outside of GCP to a destination in the network; others direct traffic from inside the network. Destinations for forwarding rules are target instances, load balancer targets \(target proxies, target pools, and backend services\), and VPN gateways.

## Types of VPC

#### Default VPC

Unless you choose to disable it, each new project starts with a `default` network. The `default` network is an auto mode network with [pre-populated firewall rules](https://cloud.google.com/vpc/docs/firewalls#default_firewall_rules). You can disable the creation of default networks by [creating an organization policy](https://cloud.google.com/resource-manager/docs/organization-policy/creating-managing-policies) with the [`compute.skipDefaultNetworkCreation` constraint](https://cloud.google.com/resource-manager/docs/organization-policy/org-policy-constraints). Projects that inherit this policy won't have a default network.

* Subnets created per region/zone.
* Internet gateway also created.
* Firewalls are opened between subnets so that all resources can communicate.

#### Auto VPC

* Single subnet per region
* Fixed /20 subnets
* Expandable up to /16
* Default Network is auto mode
* Predefined IP range

#### Custom VPC

* No default subnets
* Manually created subnets can use any value RFC1918 IP range
* Ranges do not have to be contiguous between subnets
* Full controls of IP ranges

## Reserved Addresses

| Reserved Address | Description | Example |
| :--- | :--- | :--- |
| Network | First address in the primary IP range for the subnet | `10.1.2.0` in `10.1.2.0/24` |
| Default gateway | Second address in the primary IP range for the subnet | `10.1.2.1` in `10.1.2.0/24` |
| Second-to-last address | Second-to-last address in the primary IP range for the subnet that is reserved by GCP for potential future use | `10.1.2.254` in `10.1.2.0/24` |
| Broadcast | Last address in the primary IP range for the subnet | `10.1.2.255` in `10.1.2.0/24` |

## Interfaces and IP Addresses

#### IP addresses <a id="ip_addresses"></a>

GCP resources, such as Compute Engine VM instances, forwarding rules, GKE containers, and App Engine, rely on IP addresses to communicate.

#### Alias IP ranges <a id="alias_ip_ranges"></a>

If you have multiple services running on a single VM instance, you can give each service a different internal IP address using Alias IP Ranges. The VPC network forwards packets destined for each configured alias IP to the corresponding VM.

#### Multiple Network Interfaces <a id="multiple_network_interfaces"></a>

You can add multiple network interfaces to a VM instance, where each interface resides in a unique VPC network. Multiple network interfaces enable a network appliance VM to act as a gateway for securing traffic among different VPC networks or to and from the Internet.

## Hybrid Cloud

#### VPN <a id="vpn"></a>

Allows you to connect your VPC network to your physical, on-premises network or another cloud provider using a secure[Virtual Private Network](https://wikipedia.org/wiki/Virtual_private_network).

#### Interconnect <a id="interconnect"></a>

Allows you to connect your VPC network to your on-premises network using a high speed physical connection.

## Load balancing

GCP offers the following load balancing configurations to distribute traffic and workloads across many VMs:

* Global external load balancing, including HTTP\(S\) load balancing, SSL Proxy, and TCP Proxy offerings.
* Regional, external network load balancing
* Regional internal load balancing

## Special configurations

#### Private Google Access <a id="private_google_access"></a>

Instances in a subnet of a VPC network can communicate with [Google APIs and services](https://developers.google.com/apis-explorer/) using private IP addresses instead of external IP addresses when you enable private Google access for the subnet.

