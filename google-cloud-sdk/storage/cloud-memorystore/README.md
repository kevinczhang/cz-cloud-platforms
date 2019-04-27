---
description: >-
  Cloud Memorystore for Redis provides a fully-managed service that is powered
  by the Redis in-memory data store to build application caches that provide
  sub-millisecond data access.
---

# Cloud Memorystore

### What it's good for <a id="what_its_good_for"></a>

* **Caching:** Cache is an integral part of modern application architectures. Cloud Memorystore for Redis provides low latency access and high throughput for heavily accessed data, compared to accessing the data from a disk based backend store. Session management, frequently accessed queries, scripts, and pages are common examples of caching.
* **Gaming:** Gaming is about capturing and keeping the user's attention. One key aspect that keeps users hooked on a game is the leader board. Player Profile is another piece of information that can be accessed frequently. Redis hash makes it fast and easy to store and access profile data.
* **Stream Processing:** Whether processing a Twitter feed or stream of data from IoT devices, Cloud Memorystore for Redis is a perfect fit for streaming solutions. Combined with Cloud Dataflow, Cloud Memorystore for Redis provides a scalable, fast in-memory store for storing intermediate data that thousands of clients can access with very low latency.

## Connection

In order to connect to your instance, your client must be on the same network, or peered to the same network, and located in the same region as your Cloud Memorystore for Redis instance. Clients in different zones but the same region as your Redis instance can connect to the Redis instance.

Also, if you want to connect to your Redis instance from a resource in another project using Shared VPC, your Redis instance must be deployed in the Shared VPC host project; additionally, the resource and your Redis instance must either be on the same Shared VPC network or the networks must be peered. Connecting to a Redis instance that is deployed on a shared VPC network in a service project is not supported.

## Creation

* Instance ID \(Permanent identifier for your instance. Use lowercase letters, numbers and hyphens. Start with a letter.\)
* Display name \(Optional\) For display purposes only
* Version \(4.0 \(beta\) is recommended for new instances\)
* Instance tier
  * Basic

    Lower cost. Does not provide high availability.

  * Standard

    Includes a failover replica in a separate zone for high availability. Cannot downgrade later.
* Location \(Choice is permanent. Determines where your data is stored. For better performance, keep your data close to the services that need it.\)
*  Instance capacity

  Memory provisioned for Redis usage. Affects cost. Provision enough storage for peak usage.

*  Network throughput \(MB/s\)

  Estimate based on capacity selection

*  Authorised network

  Select the network that applications will use to access your Redis instance. Access will only be allowed through this network, so your applications should also be on this network. 

*  Redis configuration

  You can customise Redis configuration parameters at any time. Updates to a running instance take effect immediately and require no downtime.

*  Instance IP address range

  Instance will be assigned an IP address within this range. Ensure that the range does not overlap with an existing VPC network's subnets or with the range used by other Redis instances in this project.





