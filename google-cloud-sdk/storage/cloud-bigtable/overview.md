# Overview

## Cloud Bigtable storage model

Cloud Bigtable stores data in massively scalable tables, each of which is a sorted key/value map. The table is composed of _rows_, each of which typically describes a single entity, and _columns_, which contain individual values for each row. Each row is indexed by a single _row key_, and columns that are related to one another are typically grouped together into a _column family_. Each column is identified by a combination of the column family and a _column qualifier_, which is a unique name within the column family.

Each row/column intersection can contain multiple _cells_, or versions, at different timestamps, providing a record of how the stored data has been altered over time. Cloud Bigtable tables are sparse; if a cell does not contain any data, it does not take up any space.

![](../../../.gitbook/assets/image%20%2824%29.png)

* **The table contains one column family,** the `follows` family. This family contains multiple column qualifiers.
* **Column qualifiers are used as data.** This design choice takes advantage of the sparseness of Cloud Bigtable tables, and the fact that new column qualifiers can be added on the fly.
* **The username is used as the row key.** Assuming usernames are evenly spread across the alphabet, data access will be reasonably uniform across the entire table. See [Load balancing](https://cloud.google.com/bigtable/docs/overview#load-balancing) to learn how Cloud Bigtable handles uneven loads and [Choosing a row key](https://cloud.google.com/bigtable/docs/schema-design#row-keys) for more advanced tips on picking a row key.

## Cloud Bigtable architecture

![Cloud Bigtable architecture](../../../.gitbook/assets/image%20%2838%29.png)

As the diagram illustrates, all client requests go through a front-end server before they are sent to a Cloud Bigtable node. ****The nodes are organized into a Cloud Bigtable cluster, which belongs to a Cloud Bigtable instance, a container for the cluster.

## Instances

A Cloud Bigtable instance is mostly just a container for your [clusters](https://cloud.google.com/bigtable/docs/instances-clusters-nodes#clusters) and [nodes](https://cloud.google.com/bigtable/docs/instances-clusters-nodes#nodes), which do all of the real work. Tables belong to instances, not to clusters or nodes. 

### Clusters <a id="clusters"></a>

A cluster represents the actual Cloud Bigtable service. Each cluster belongs to a single Cloud Bigtable instance, and an instance can have up to 4 clusters. When your application sends requests to a Cloud Bigtable instance, those requests are actually handled by one of the clusters in the instance.

Each cluster is located in a single zone. An instance's clusters must be in unique zones. You can create an additional cluster in any zone where Cloud Bigtable is available. 

### Nodes <a id="nodes"></a>

Behind the scenes, Cloud Bigtable splits all of the data from your tables into smaller _tablets_. Tablets are stored on disk, separate from the nodes but in the same zone as the nodes. Each node is responsible for keeping track of specific tablets on disk; handling incoming reads and writes for its tablets; and performing maintenance tasks on its tablets, such as periodic [compactions](https://cloud.google.com/bigtable/docs/overview#compactions). Each tablet is associated with a single node.

