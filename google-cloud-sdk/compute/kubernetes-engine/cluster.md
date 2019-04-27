---
description: >-
  In Google Kubernetes Engine, a cluster consists of at least one cluster master
  and multiple worker machines called nodes. These master and node machines run
  the Kubernetes cluster orchestration system
---

# Cluster

### Cluster master <a id="master"></a>

The _cluster master_ runs the Kubernetes control plane processes, including the Kubernetes API server, scheduler, and core resource controllers. The master's lifecycle is managed by GKE when you [create](https://cloud.google.com/kubernetes-engine/docs/how-to/creating-a-container-cluster) or [delete](https://cloud.google.com/kubernetes-engine/docs/how-to/deleting-a-container-cluster) a cluster. 

#### Cluster master and the Kubernetes API <a id="master_api"></a>

The master is the unified endpoint for your cluster. All interactions with the cluster are done via Kubernetes API calls, and the master runs the **Kubernetes API Server** process to handle those requests. You can make Kubernetes API calls directly via HTTP/gRPC, or indirectly, by running commands from the Kubernetes command-line client \(`kubectl`\) or interacting with the UI in the GCP Console.

### Nodes <a id="nodes"></a>

A cluster typically has one or more _nodes_, which are the worker machines that run your containerized applications and other workloads. The individual machines are [Compute Engine VM instances](https://cloud.google.com/compute/docs/instances/) that GKE creates on your behalf when you create a cluster.

 A node runs the services necessary to support the Docker containers that make up your cluster's workloads. These include the Docker runtime and the Kubernetes node agent \(`kubelet`\) which communicates with the master and is responsible for starting and running Docker containers scheduled on that node.

## Node pools

A **node pool** is a group of \[nodes\] within a cluster that all have the same configuration. Node pools use a [NodeConfig](https://cloud.google.com/kubernetes-engine/docs/reference/rest/v1/NodeConfig) specification. You cannot configure a single node in a node pool; any configuration changes affect all nodes in the node pool.

