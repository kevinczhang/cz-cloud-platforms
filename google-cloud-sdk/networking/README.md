# Networking

## What is BBR?

BBR \("**B**ottleneck **B**andwidth and **R**ound-trip propagation time"\) is a new congestion control algorithm developed at Google. Congestion control algorithms — running inside every computer, phone or tablet connected to a network — that decide how fast to send data.

## Networks, firewalls, and routes

[Virtual Private Cloud \(VPC\)](https://cloud.google.com/vpc/docs) provides a set of networking services that your VM instances use. Each instance can be attached to only one network. Every VPC project has a _default network_. You can create additional networks in your project, but networks cannot be shared between projects.

* Auto Mode: Subnets created automatically
* Custom Mode: Subnets created manually

[_Firewall rules_](https://cloud.google.com/vpc/docs/firewalls) govern traffic coming into instances on a network. The default network has a default set of firewall rules, and you can create custom rules, too.

A [_route_](https://cloud.google.com/vpc/docs/routes) lets you implement more advanced networking functions in your instances, such as creating VPNs. A route specifies how packets leaving an instance should be directed. For example, a route might specify that packets destined for a particular network range should be handled by a gateway virtual machine instance that you configure and operate.

## Load balancing

If your website or application is running on Compute Engine, the time might come when you're ready to distribute the workload across multiple instances. Server-side [load balancing](https://cloud.google.com/load-balancing/docs) features provide you with the following options:

* [Network load balancing](https://cloud.google.com/load-balancing/docs/network/) lets you distribute traffic among server instances in the same region based on incoming IP protocol data, such as address, port, and protocol. Network load balancing is a great solution if, for example, you want to meet the demands of increasing traffic to your website.
* [HTTP/HTTPS load balancing](https://cloud.google.com/load-balancing/docs/https/) enables you to [distribute traffic across regions](https://cloud.google.com/load-balancing/docs/https/cross-region-example) so you can ensure that requests are routed to the closest region or, in the event of a failure or over-capacity limitations, to a healthy instance in the next closest region. You can also use HTTP/HTTPS load balancing to [distribute traffic based on content type](https://cloud.google.com/load-balancing/docs/https/content-based-example). For example, you might set up your servers to deliver static content, such as images and CSS, from one server and dynamic content, such as PHP pages, from a different server. The load balancer can direct each request to the server that provides each content type.

## Cloud DNS

You can publish and maintain [Domain Name System \(DNS\)](https://cloud.google.com/dns/docs/) records by using the same infrastructure that Google uses. You can use the Google Cloud Platform Console, the command line, or a REST API to work with managed zones and DNS records.

