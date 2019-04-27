# Instance Groups

Instance Groups allow you to think about a group of instances as single entity. There are two types of instance groups: Managed and Unmanaged Instance Groups. To create a new Instance group:

1. **Location** \(Single zone needs a Region and a Zone. Multiple zones need a Region and multiple zones.\)
2. **Port name mapping** \(A load balancer sends traffic to an instance group through a named port. Create a named port to map the incoming traffic to a specific port number and then go to "HTTP load balancing" to create a load balancer using this instance group.\)
3. **Instance group type** \(details below\)
4. **Instance template** \(parameters same as creating VM instance\)
5. **Auto-scaling** \(On or Off\)
6. **Auto - scaling policy** \(CPU usage, HTTP load balancing usage, Stackdriver monitoring metric, Multiple metrics\)
7. **Auto-healing** \(Auto-healing allows recreating VM instances when needed. You can use a health check to recreate a VM instance if the health check finds it unresponsive. If you don't select a health check, Compute Engine will recreate VM instances only when they're not running.\)
8. **Health Check** \(A health check determines whether a VM instance is healthy by sending HTTP requests to the instance. An instance is considered healthy if it returns consecutive responses within a specified time. Health checks are used for load balancing and auto-scaling managed instance groups.\)

## Instance group type

#### Managed Instance Groups

Allow us to create a template for an instance and then autoscale based on some metrics \(CPU, HTTP load balancing, Stackdriver, etc\). The number of instances in the group will increase or decrease based on a template. Using a template, all the instances will look identical. VM instances are stateless and disks are deleted upon VM deletion or recreation.

#### Unmanaged Instance Groups

Don't require the use of a template. Allowing us to create a group and load balance based on existing instances that use different configurations. This should only be used if you can't use a managed instance group. Auto-scaling, auto-healing and rolling updating are not supported.

