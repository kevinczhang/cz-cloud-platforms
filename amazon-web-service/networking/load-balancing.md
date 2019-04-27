# Load Balancing

## Load balancer

* Load balancing \(as a concept\) is a common method used for distributing incoming traffic among servers.
* An Elastic Load Balancer is an EC2 service that automates the process of distributing incoming traffic \(evenly\) to all the instances that are associated with ELB.
* An elastic load balancer can load balance traffic to multiple EC2 instances located across multiple availability zones. This allows for highly availability and fault tolerant architecture.
* Elastic load balancing should be paired with Auto scaling to enhance high availability and fault tolerance, AND allow for automated scalability and elasticity.
* An ELB has its own DNS record set that allows for direct access from the open internet access.

### Important ELB facts

* When used within a VPC, an ELB can act as an internal load balancer and load balance to internal EC2 instances on private subnets \(as often done with multi-tier applications\).
* ELBs will automatically stop serving traffic to an instance that becomes unhealthy \(via health checks\).
* An ELB can help reduce compute power on an EC2 instance by allowing for an SSL certificate to be applied directly to the elastic load balancer.

### Application Elastic Load Balancer 

* An "Application" elastic load balancer is designed for **complex** balancing of traffic to multiple EC2 instances using **Content-based "rules"**.
* Content-based rules \(setup on the listener\) can be configured using:
  * **Host-based rules**: Route traffic based on the host field of the HTTP header
  * **Path-based rules**: Route traffic based on the URL path of the HTTP header
  * This allows you to structure your application as smaller services, and even monitor/auto-scale based on traffic to specific "**target groups**"
* An Application ELB also supports ECS Containers, HTTP, HTTP/2, WebSockets, Access logs, Sticky Sessions, and AWS WAF \(Web Application Firewall\).

## Auto Scaling

Auto scaling is a service \(and method\) provided by AWS that automates the process of increasing or decreasing the number of provisioned on-demand instances available for your application based on chosen **Cloudwatch** metrics.

#### Auto scaling has two main components

1. Launch Configuration: The EC2 "template" used when auto scaling group needs to provision an additional instance \(i.e. AMI, instance type, user-data, storage, security groups, etc\).
2. Auto scaling group: all the rules and settings that goven if/when an EC2 instance is automatically provisioned or terminated:
   1. Number of MIN & MAX allows instances
   2. VPC & AZs to launch instances into
   3. If provisioned instances should receive traffic from a ELB
   4. Scaling policies \(cloudwatch metrics thresholds that trigger scaling\)
   5. SNS notifications \(to keep you informed when scaling occurs\)

