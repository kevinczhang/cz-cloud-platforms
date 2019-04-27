---
description: >-
  Mission-critical, relational database service with transactional consistency,
  global scale, and high availability.
---

# Cloud Spanner

Good for:

* Mission-critical applications
* High transactions
* Scale + consistency requirements

Common workloads:

* Adtech
* Financial services
* Global supply chain
* Retail

Instance creation includes two important choices: the _instance configuration_ and the _node count_. These choices determine the location and amount of the instance's serving and storage resources. Your configuration choice is permanent for an instance, but you can change the node count later if needed.

### Instance configuration <a id="configuration"></a>

 An instance configuration defines the geographic placement and replication of the databases in that instance. When you create an instance, you must configure it as either _regional_ \(that is, all the resources are contained within a single GCP [region](https://cloud.google.com/docs/geography-and-regions)\) or _multi-region_ \(that is, the resources span more than one region\). 

### Node count <a id="node_count"></a>

 In addition to choosing where your data is stored when you create an instance, you must also choose the **node count**, or the number of nodes to allocate to that instance. Your choice of node count determines the amount of serving and storage resources that are available to the databases in that instance.

#### Nodes vs replicas <a id="nodes_vs_replicas"></a>

The total number of servers in a Cloud Spanner instance is the number of nodes the instance has multiplied by the number of replicas in the instance.

