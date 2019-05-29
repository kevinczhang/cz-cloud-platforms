# Routes and Firewall Rules

## Routes

Routes tell VM instances and the VPC network how to send traffic from an instance to a destination, either inside the network or outside of GCP. Each VPC network comes with some [system generated routes](https://cloud.google.com/vpc/docs/vpc#system-generated-routes) to route traffic among its subnets and send traffic from [eligible instances](https://cloud.google.com/vpc/docs/vpc#internet_access_reqs) to the Internet.

## Forwarding rules

While routes govern traffic leaving an instance, forwarding rules direct traffic _to_ a GCP resource in a VPC network based on IP address, protocol, and port.

Some forwarding rules direct traffic from outside of GCP to a destination in the network; others direct traffic from inside the network. Destinations for forwarding rules are target instances, load balancer targets \(target proxies, target pools, and backend services\), and VPN gateways.

## Firewall rules

Each VPC network implements a distributed virtual firewall that you can configure. Firewall rules allow you to control which packets are allowed to travel to which destinations. Every VPC network has two [implied firewall rules](https://cloud.google.com/vpc/docs/firewalls#default_firewall_rules) that **block all incoming connections** and **allow all outgoing connections**.

The `default` network has [additional firewall rules](https://cloud.google.com/vpc/docs/firewalls#default_firewall_rules), including the `default-allow-internal` rule, which permit communication among instances in the network.







