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



### Comparing options <a id="comparing_options"></a>

Google offers options for platform-as-a-service \(PaaS\), containers, and infrastructure-as-a-service \(IaaS\). The following table lists and describes the options:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Product</th>
      <th style="text-align:left">Your needs</th>
      <th style="text-align:left">Product features</th>
      <th style="text-align:left">Typical use cases</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><a href="https://cloud.google.com/appengine/"><img src="https://cloud.google.com/images/appengine-icon-54x48.png" alt="Google App Engine"/></a> 
          <br
          /><a href="https://cloud.google.com/appengine/"><b>Google App Engine</b></a>
        </p>
        <p>A flexible, zero ops platform for building highly available apps</p>
      </td>
      <td style="text-align:left">
        <ul>
          <li>You want to <b>focus on writing code</b>, and never want to touch a server,
            cluster, or infrastructure.</li>
          <li>You want to build a <b>highly reliable and scalable serving app or component</b>without
            doing it all yourself.</li>
          <li>You value <b>developer velocity</b> over infrastructure control.</li>
          <li>You want to <b>minimize operational overhead</b>.</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>A range of curated serving stacks with smart defaults and deep customizability.</li>
          <li>Support for Java, Python, PHP, Go, Ruby, Node.js, and ASP.NET Core (beta)
            ... or bring your own app runtime.</li>
          <li>Integrated SDK, managed services, and local development environment.</li>
          <li>App versioning with zero-downtime upgrades.</li>
          <li>Traffic splitting.</li>
          <li>Automatic high availability with built-in auto-scaling.</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Web sites.</li>
          <li>Mobile app and gaming backends.</li>
          <li>RESTful APIs.</li>
          <li>Internal Line of Business (LOB) apps.</li>
          <li>Internet of things (IoT) apps.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><a href="https://cloud.google.com/kubernetes-engine/"><img src="https://cloud.google.com/images/container-icon-54x48.png" alt="Google Kubernetes Engine"/></a> 
          <br
          /><a href="https://cloud.google.com/kubernetes-engine/"><b>Google Kubernetes Engine</b></a>
        </p>
        <p>Logical infrastructure powered by <a href="http://kubernetes.io/">Kubernetes</a>,
          the open source container orchestration system.</p>
      </td>
      <td style="text-align:left">
        <ul>
          <li>You want to <b>increase velocity and improve operability dramatically</b> by
            separating the app from the OS.</li>
          <li>You need a secure, scalable way to <b>manage containers in production.</b>
          </li>
          <li>You <b>don&#x2019;t have dependencies on a specific operating system.</b>
          </li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Logical infrastructure - focus on your app components, not virtual machines.</li>
          <li>Easy mechanisms for building loosely-coupled distributed systems.</li>
          <li>Run the same application on your laptop, on premise and in the cloud.</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Containerized workloads.</li>
          <li>Cloud-native distributed systems.</li>
          <li>Hybrid applications.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><a href="https://cloud.google.com/compute/"><img src="https://cloud.google.com/images/compute-icon-54x48.png" alt="Google Compute Engine"/></a> 
          <br
          /><a href="https://cloud.google.com/compute/"><b>Google Compute Engine</b></a>
        </p>
        <p>Virtual machines running in Google&apos;s global data center network</p>
      </td>
      <td style="text-align:left">
        <ul>
          <li><b>You need complete control</b> over your infrastructure and direct access
            to high-performance hardware such as GPUs and local SSDs.</li>
          <li><b>You need to make OS-level changes</b>, such as providing your own network
            or graphic drivers, to squeeze out the last drop of performance.</li>
          <li>You want to move your application from your own colo or datacenter to
            the cloud without rewriting it.</li>
          <li>You need to run a software package that can&#x2019;t easily be containerized
            or you <b>want to use existing VM images</b>.</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Virtual machines with network-attached and ultra-high performance local
            storage options.</li>
          <li>Preemptible virtual machines for inexpensive batch jobs and fault-tolerant
            workloads.</li>
          <li>Customizable load-balancing and auto-scaling across homogeneous VMs.</li>
          <li>Direct access to GPUs that you can use to accelerate specific workloads.</li>
          <li>Support for the most popular flavors of Linux and Windows operating systems.</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Any workload requiring a specific OS or OS configuration.</li>
          <li>Currently deployed, on-premises software that you want to run in the cloud.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>### Combining multiple options <a id="combining_multiple_options"></a>

You don't need to restrict yourself to a single computing choice for your whole application. You can mix options, choosing the right approach for any application component and connect them together. For example, you can:

* Use App Engine for the front end serving layer, while running Redis in Compute Engine.
* Use Container Engine for a rendering microservice that uses Compute Engine VMs running Windows to do the actual frame rendering.
* Use App Engine for your web front end, Cloud SQL as your database, and Container Engine for your big data processing.

