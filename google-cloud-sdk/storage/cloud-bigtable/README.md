---
description: >-
  A scalable, fully managed NoSQL wide-column database that is suitable for both
  low-latency single-point lookups and precalculated analytics.
---

# Cloud BigTable

Cloud Bigtable is a sparsely populated table that can scale to billions of rows and thousands of columns, enabling you to store terabytes or even petabytes of data. A single value in each row is indexed; this value is known as the row key. Cloud Bigtable is ideal for storing very large amounts of single-keyed data with very low latency. It supports high read and write throughput at low latency, and it is an ideal data source for MapReduce operations. 

Cloud Bigtable also excels as a storage engine for batch MapReduce operations, stream processing/analytics, and machine-learning applications.

Good for:

* Low-latency read/write access
* High-throughput data processing
* Time series support

Common workloads:

* IoT, finance, adtech
* Personalization, recommendations
* Monitoring
* Geospatial datasets
* Graphs

## Bigtable creation

1. Instance name \(display purpose only\)
2. Instance ID \(ID is permanent\)
3. Instance type
   1. Production \(Minimum of 3 nodes. High availability. Cannot downgrade later.\) 
   2. Development \(Low-cost instance for development and testing. Does not provide high availability or replication. Can upgrade to Production later.\)
4. Storage type \(Choice is permanent. Applies to all clusters. Affects cost.\)
   1. SSD \(Lower latency and more rows read per second. Typically used for real-time serving use cases, such as ad serving and mobile app recommendations.\)
   2. HDD \(Higher latency for random reads. Good performance on scans and typically used for batch analytics, such as machine learning or data mining.\)
5. Clusters
   1. Cluster ID \(permanent\)
   2. Location \(Choice is permanent. Determines where cluster data is stored. To reduce latency and increase throughput, store your data near the services that need it.\)
   3. Nodes \(Add nodes to increase your cluster's capacity for data throughput, storage and rows read per second. Add enough to keep each cluster's CPU utilisation under the recommended threshold for your current number of clusters and [app profile routing policy](https://cloud.google.com/bigtable/docs/app-profiles?hl=en_GB#routing).\)
   4. Performance \(Based on current node count and storage type.

      Adding a cluster increases read throughput but not write throughput. When writing, Cloud Bigtable uses the additional throughput for replication.

      Reads: 1,500 rows/s @ 200 msorWrites: 30,000 rows/s @ 50 msorScans: 540 MB/s

      Storage: 24 TB\)
6. Replication guidance \(Replication for Cloud Bigtable copies your data across multiple regions, enabling you to isolate workloads and increase the availability and durability of your data.\)
   * Replication cannot be paused. All writes are automatically replicated to all clusters.
   * Replication uses a primary-primary configuration with eventual consistency.
   * Replicating writes between clusters requires additional CPU for each cluster in the instance.
   * Provision enough nodes for each cluster to keep the cluster's average CPU utilisation under the recommended threshold for your current number of clusters and app profile policy. For instances with 1 cluster or multiple clusters and single-cluster routing, keep average CPU utilisation under 70%. For instances with 2 clusters and multi-cluster routing, keep CPU utilisation under 35%. For instances with more than 2 clusters and multi-cluster routing, see [additional configuration guidance](https://cloud.google.com/bigtable/docs/replication-settings?hl=en_GB).
   * Routing and other client access patterns are configured by the application profile. If needed, you can create and customise additional profiles.

