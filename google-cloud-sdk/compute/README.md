# Compute

![](../../.gitbook/assets/image%20%2838%29.png)

![](../../.gitbook/assets/image%20%2831%29.png)

## Serverless computing

[Google Cloud Functions](https://cloud.google.com/functions/docs/concepts/overview), GCP's _functions as a service_ \(FaaS\) offering, provides a serverless execution environment for building and connecting cloud services. With Cloud Functions, you write simple, single-purpose functions that are attached to events raised by your cloud infrastructure and services. Your Cloud Function runs when a watched event is raised. Your code executes in a fully managed environment; you don't need to provision any infrastructure or worry about managing any servers.

Cloud Functions are a good choice for use cases that include:

* Data processing and ETL operations, for scenarios such as video transcoding and IoT streaming data.
* Webhooks to respond to HTTP triggers.
* Lightweight APIs that comprise loosely coupled logic into applications.
* Mobile backend functions.

## Application platform

Google App Engine is GCP's _platform as a service_ \(PaaS\). With App Engine, Google handles most of the management of the resources for you. 

For example, if your application requires more computing resources because traffic to your website increases, Google automatically scales the system to provide those resources. If the system software needs a security update, that's handled for you, too.

## Containers

With container-based computing, you can focus on your application code, instead of on deployments and integration into hosting environments. Google Kubernetes Engine, GCP's _containers as a service_ \(CaaS\) offering, is built on the open source [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) system, which gives you the flexibility of on-premises or hybrid clouds, in addition to GCP's public cloud infrastructure.

When you build with Kubernetes Engine, you can:

* Create and manage groups of Compute Engine instances running Kubernetes, called [_clusters_](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture). Kubernetes Engine uses Compute Engine instances as [_nodes_](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture#nodes) in a cluster. Each node runs the Docker runtime, a Kubernetes node agent that monitors the health of the node, and a simple network proxy.
* Declare the requirements for your Docker containers by creating a simple JSON configuration file.
* Use Google Container Registry for secure, private storage of Docker images. You can [push images to your registry](https://cloud.google.com/container-registry/docs/pushing-and-pulling) and then you can pull images to any Compute Engine instance or your own hardware by using an HTTP endpoint.
* Create single- and multi-container [_pods_](https://cloud.google.com/kubernetes-engine/docs/concepts/pod). Each pod represents a logical host that can contain one or more containers. Containers in a pod work together by sharing resources, such as networking resources. Together, a set of pods might comprise an entire application, a micro-service, or one layer in a multi-tier application.
* Create and manage \_[replication controllers](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/)\_, which manage the creation and deletion of pod replicas based on a template. Replication controllers help to ensure that your application has the resources it needs to run reliably and scale appropriately.
* Create and manage \_[services](https://kubernetes.io/docs/concepts/services-networking/service/)\_. Services create an abstraction layer that decouples frontend clients from pods that provide backend functions. In this way, clients can work without concerns about which pods are being created and deleted at any given moment.
* Create an external network load balancer.

## Virtual machines

GCP's unmanaged compute service is Google Compute Engine. You can think of Compute Engine as providing an _infrastructure as a service_ \(IaaS\), because the system provides a robust computing infrastructure, but you must choose and configure the platform components that you want to use. With Compute Engine, it's your responsibility to configure, administer, and monitor the systems. Google will ensure that resources are available, reliable, and ready for you to use, but it's up to you to provision and manage them. The advantage, here, is that you have complete control of the systems and unlimited flexibility.

When you build on Compute Engine, you can:

* Use virtual machines \(VMs\), called [_instances_](https://cloud.google.com/compute/docs/instances), to build your application, much like you would if you had your own hardware infrastructure. You can choose from a variety of instance types to customize your configuration to meet your needs and your budget.
* Choose which global [regions and zones](https://cloud.google.com/compute/docs/zones) to deploy your resources in, giving you control over where your data is stored and used.
* Choose which operating systems, development stacks, languages, frameworks, services, and other software technologies you prefer.
* Create instances from public or private [images](https://cloud.google.com/compute/docs/images) .
* Use GCP storage technologies or any third-party technologies you prefer.
* Use [Google Cloud Launcher](https://cloud.google.com/launcher) to quickly deploy pre-configured software packages. For example, you can deploy a LAMP or MEAN stack with just a few clicks.
* Create [instance groups](https://cloud.google.com/compute/docs/instance-groups) to more easily manage multiple instances together.
* Use [autoscaling with an instance group](https://cloud.google.com/compute/docs/autoscaler) to automatically add and remove capacity.
* Attach and detach [disks](https://cloud.google.com/compute/docs/disks) as needed.
* [Use SSH to connect](https://cloud.google.com/compute/docs/instances/connecting-to-instance) directly to your instances.

