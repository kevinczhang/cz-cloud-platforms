---
description: >-
  Google Kubernetes Engine, GCP's containers as a service (CaaS) offering, is
  built on the open source Kubernetes system, which gives you the flexibility of
  on-premises or hybrid clouds, in addition to
---

# Kubernetes Engine

Kubernetes is a cluster of servers/nodes, which has some processes/pods, which has ip addresses and is running containers. We can control pods using controllers, like deployment controller \(how to deploy\), daemontSet controller \(one on each pod\) refer to workload section. Services act as the entrypoints for Kubernetes cluster.

![](../../../.gitbook/assets/image%20%284%29.png)

## Kubernetes cluster types

* Clone an existing cluster
* Standard cluster
* CPU intensive applications
* Memory intensive applications
* GPU Accelerated Computing
* Highly available

## GKE creation

#### Location Type \(Zonal and Regional with Master version\)

A regional cluster provides a single static endpoint for the entire cluster, enabling you to access the cluster's control plane regardless of any outage or downtime in an individual zone.

#### Node pools

Node pools are separate instance groups running Kubernetes in a cluster. You may add node pools in different zones for higher availability, or add node pools of different machine types.

1. Node version
2. Number of nodes \(optional auto-scaling\)
3. Image type \(Container-Optimised OS \(cos\), cos with Containerd\(beta\), Ubuntu\).
4. Machine Type \(CPU and memory\)
5. Boot disk type \(Standard persistent disk, SSD persistent disk\)
6. Boot disk size \(GB\)
7. Local SSD disks \(optional and with option for pre-emptible nodes\)
8. Management \(options for auto-upgrade and auto-repair\)
9. Security \(Service account, Access scopes \(Allow default access, Allow full access to all Cloud APIs, Set access for each API\)\)
10. Metadata
    1. Kubernetes labels \(These labels are applied to every Kubernetes node in this node pool. Kubernetes node labels can be used in node selectors to control how workloads are scheduled to your nodes.\)
    2. Node taints \(beta\) \(These settings will be applied to every Kubernetes node in this node pool. Kubernetes taints can be used together with tolerations to control how workloads are scheduled to your nodes\)
    3. GCE instance metadata \(These items will appear in the Compute Engine instance metadata of every node in this node pool.\)
11. Availability 
    * Additional node locations \(Additional node zones must be from the same region as the original zone. Kubernetes Engine allocates the same resource footprint for each zone.\)
    * Maintenance window \(beta\) \(These settings will be applied to every Kubernetes node in this node pool. Kubernetes taints can be used together with tolerations to control how workloads are scheduled to your nodes\)
12. Networking
    1. **VPC-native** \(This feature uses alias IP and provides a more secure and native integration with Google Cloud Platform services.\)
    2. Network \(The network that the Kubernetes cluster is in determines which other Compute Engine resources it is able to communicate with. Network is permanent.\)
    3. Subnet \(Subnetwork to which the Kubernetes cluster will belong. Subnet is permanent.\)
    4. Pod address range \(All pods in the cluster are assigned an IP address from this range. Enter a range \(in CIDR notation\) within a network range \(RFC 1918\) or leave this field blank to use a default range.\)
    5. Enable Intranode visibility \(beta\) \(Reveals your intranode traffic to Google's networking fabric. To obtain logs, you need to enable VPC flow logs in the [selected subnetwork](https://console.cloud.google.com/networking/subnetworks/details/us-central1/default?project=linen-creek-237819).\)
    6. Load balancing 
    7. Network security
       1. Private cluster \(Nodes don't have public IP and master not accessible from outside\)
       2. Enable master authorised networks \(Enable master authorised networks to block untrusted non-GCP source IPs from accessing the Kubernetes master through HTTPS.\)
       3. Enable network policy \(The Kubernetes Network Policy API allows the cluster administrator to specify which pods are allowed to communicate with each other. Google Kubernetes Engine has partnered with Tigera to provide [Project Calico ](https://www.projectcalico.org/) to enforce network policies within your cluster.\)
13. Security 
    * Enable legacy authorisation \(Enable legacy authorisation for in-cluster permissions that support existing clusters or workflows. Disable legacy authorisation for full RBAC support for in-cluster permissions.\)
    * Enable Binary Authorization \(beta\) \(Allows policy control over images deployed to GKE\).
    * Enable Application-layer Secrets Encryption \(beta\) \(Application-layer Secrets Encryption protects your secrets in etcd with a key that you manage in [Cloud KMS](https://console.cloud.google.com/security/kms?project=linen-creek-237819). Note that secrets are already encrypted at the storage layer.\)
14. **Metadata \(**To organise your project, add arbitrary labels as key/value pairs to your resources. Use labels to indicate different environments, services, teams and so on.**\)**
15. **Stackdriver \(**Enable Stackdriver Logging service or Enable Stackdriver Monitoring service**\)**
16. **Additional features**
    1. Enable Cloud TPU
    2. Enable Kubernetes alpha features in this cluster
    3. Enable Kubernetes Dashboard
    4. Enable Istio \(beta\) \(Istio is a service mesh that provides monitoring, traffic control and security between the services running in Kubernetes Engine. If enabled, the Istio components will be installed in your cluster.\)
    5. Enable Cloud Run on GKE \(beta\)
    6. Enable node auto-provisioning \(beta\)
    7. Enable Vertical Pod Auto-scaling \(beta\)

## When to use Kubernetes Engine

#### Containerized workloads, app-focused, distributed systems, hybrid

* You' re running containerized workloads.
* You care about containers rather than the underlying OS
* You care about application portability
* You want to focus on containers as a unit of deployment

![](../../../.gitbook/assets/image%20%2827%29.png)

When you build with Kubernetes Engine, you can:

* Create and manage groups of Compute Engine instances running Kubernetes, called [_clusters_](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture). Kubernetes Engine uses Compute Engine instances as [_nodes_](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture#nodes) in a cluster. Each node runs the Docker runtime, a Kubernetes node agent that monitors the health of the node, and a simple network proxy.
* Declare the requirements for your Docker containers by creating a simple JSON configuration file.
* Use Google Container Registry for secure, private storage of Docker images. You can [push images to your registry](https://cloud.google.com/container-registry/docs/pushing-and-pulling) and then you can pull images to any Compute Engine instance or your own hardware by using an HTTP endpoint.
* Create single- and multi-container [_pods_](https://cloud.google.com/kubernetes-engine/docs/concepts/pod). Each pod represents a logical host that can contain one or more containers. Containers in a pod work together by sharing resources, such as networking resources. Together, a set of pods might comprise an entire application, a micro-service, or one layer in a multi-tier application.
* Create and manage \_[replication controllers](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/)\_, which manage the creation and deletion of pod replicas based on a template. Replication controllers help to ensure that your application has the resources it needs to run reliably and scale appropriately.
* Create and manage \_[services](https://kubernetes.io/docs/concepts/services-networking/service/)\_. Services create an abstraction layer that decouples frontend clients from pods that provide backend functions. In this way, clients can work without concerns about which pods are being created and deleted at any given moment.
* Create an external network load balancer.

## Steps to deploy code to GKE

1. Build Docker image containing our code
2. Push image to Google Container Registry
3. Deploy container into Pod through a Kubernetes Deployment resource
4. Pull environment variables from ConfigMap
5. Pull the service account key from a volume mount
6. Create a service in front of the deployment

