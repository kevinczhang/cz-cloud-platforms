---
description: >-
  The Kubernetes networking model relies heavily on IP addresses. Services,
  Pods, containers, and nodes communicate using IP addresses and ports.
---

# Network

* **ClusterIP:** The IP address assigned to a Service. 
* **Pod IP:** The IP address assigned to a given Pod.
* **Node IP:** The IP address assigned to a given node.

### Networking Inside the Cluster <a id="inside-cluster"></a>

This diagram shows a single node running two Pods, each attached to two volumes.

![](../../../.gitbook/assets/image%20%2815%29.png)

#### Services <a id="services"></a>

 In Kubernetes, you can assign arbitrary key-value pairs called [labels](https://cloud.google.com/kubernetes-engine/docs/how-to/creating-managing-labels) to any Kubernetes resource. Kubernetes uses labels to group multiple related Pods into a logical unit called a Service. A Service has a stable IP address and ports, and provides load balancing among the set of Pods whose labels match all the labels you define in the [label selector](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/#label-selectors) when you create the Service.

![](../../../.gitbook/assets/image%20%2813%29.png)

When you configure a Service, you can optionally remap its listening port by defining values for `port` and `targetPort`.

* The `port` is where clients reach the application.
* The `targetPort` is the port where the application is actually listening for traffic within the Pod.

`kube-proxy` manages this port remapping by adding and removing `iptables` rules on the node.

### Networking Outside the Cluster <a id="outside-cluster"></a>

 By default, Pods do not expose an external IP address, because `kube-proxy` manages all traffic on each node. Pods and their containers can communicate freely, but connections outside the cluster cannot access the Service.

GKE provides three different types of Load Balancers to control access and to spread incoming traffic across your cluster as evenly as possible.

* [**External Load Balancers** ](https://cloud.google.com/kubernetes-engine/docs/concepts/network-overview#ext-lb)manage traffic coming from outside the cluster and outside your GCP Virtual Private Cloud \(VPC\) network. They use forwarding rules associated with the GCP network to route traffic to a Kubernetes node.
* [**Internal Load Balancers**](https://cloud.google.com/kubernetes-engine/docs/concepts/network-overview#int-lb) manage traffic coming from within the same VPC network. Like external load balancers, they use forwarding rules associated with the GCP network to route traffic to a Kubernetes node.
* [**HTTP\(S\) Load Balancers**](https://cloud.google.com/kubernetes-engine/docs/concepts/network-overview#https-lb) are specialized external load balancers used for HTTP\(S\) traffic. They use an Ingress resource rather than a forwarding rule to route traffic to a Kubernetes node.

## Services

The idea of a [Service](https://kubernetes.io/docs/concepts/services-networking/service/) is to group a set of Pod endpoints into a single resource. Services allow your deployments to receive traffic. 

 A Service identifies its member Pods with a selector. For a Pod to be a member of the Service, the Pod must have all of the labels specified in the selector. A [label](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) is an arbitrary key/value pair that is attached to an object.

There are five types of Services:

* **ClusterIP \(default\):** Internal clients send requests to a stable internal IP address.
* **NodePort:** Clients send requests to the IP address of a node on one or more `nodePort` values that are specified by the Service.
* **LoadBalancer:** Clients send requests to the IP address of a network load balancer.
* **ExternalName:** Internal clients use the DNS name of a Service as an alias for an external DNS name.
* **Headless:** You can use a [headless service](https://kubernetes.io/docs/concepts/services-networking/service/#headless-services) in situations where you want a Pod grouping, but don't need a stable IP address.

