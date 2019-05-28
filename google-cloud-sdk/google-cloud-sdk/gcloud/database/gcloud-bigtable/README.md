---
description: Manage your Cloud Bigtable storage.
---

# gcloud bigtable

 `gcloud bigtable` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/bigtable/#GROUP) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/bigtable/#GCLOUD-WIDE-FLAGS) `…`\]

 `GROUP` is one of the following:

* [`app-profiles`](https://cloud.google.com/sdk/gcloud/reference/bigtable/app-profiles)Manage Cloud Bigtable app profiles.
* [`clusters`](https://cloud.google.com/sdk/gcloud/reference/bigtable/clusters)Manage Cloud Bigtable clusters.
* [`instances`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances)Manage Cloud Bigtable instances.

## gcloud beta bigtable app-profiles

 `gcloud beta bigtable app-profiles` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/app-profiles/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/app-profiles/#GCLOUD-WIDE-FLAGS) `…`\]

 `COMMAND` is one of the following:

* [`create`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/app-profiles/create)`(BETA)` Create a new Bigtable app profile.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/app-profiles/delete)`(BETA)` Delete a Bigtable app profile.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/app-profiles/describe)`(BETA)` Describe an existing Bigtable app profile.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/app-profiles/list)`(BETA)` List Bigtable app profiles.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/app-profiles/update)`(BETA)` Update a Bigtable app profile.

## gcloud beta bigtable clusters

 `gcloud beta bigtable clusters` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/clusters/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/clusters/#GCLOUD-WIDE-FLAGS) `…`\]

 `COMMAND` is one of the following:

* [`create`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/clusters/create)`(BETA)` Create a bigtable cluster.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/clusters/delete)`(BETA)` Delete a bigtable cluster.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/clusters/describe)`(BETA)` Describe an existing Bigtable cluster.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/clusters/list)`(BETA)` List existing Bigtable clusters.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/beta/bigtable/clusters/update)`(BETA)` Update a Bigtable cluster's number of nodes.

## gcloud bigtable instances

 `gcloud bigtable instances` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/#GCLOUD-WIDE-FLAGS) `…`\]

 `COMMAND` is one of the following:

* [`add-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/add-iam-policy-binding)Add an IAM policy binding to a Cloud Bigtable instance.
* [`create`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/create)Create a new Bigtable instance.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/delete)Delete an existing Bigtable instance.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/describe)Describe an existing Bigtable instance.
* [`get-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/get-iam-policy)Get the IAM policy for a Cloud Bigtable instance.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/list)List existing Bigtable instances.
* [`remove-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/remove-iam-policy-binding)Remove an IAM policy binding from a Cloud Bigtable instance.
* [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/set-iam-policy)Set the IAM policy for a Cloud Bigtable instance.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/update)Modify an existing Bigtable instance.
* [`upgrade`](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/upgrade)Upgrade an existing instance's type from development to production.

1. Start by creating an instance with a single cluster. Use the [`bigtable instances create` command](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/create) to create an instance:

   ```text
   gcloud bigtable instances create INSTANCE_ID \
       --cluster=CLUSTER_ID \
       --cluster-zone=CLUSTER_ZONE \
       --display-name=DISPLAY_NAME \
       [--cluster-num-nodes=CLUSTER_NUM_NODES] \
       [--cluster-storage-type=CLUSTER_STORAGE_TYPE] \
       [--instance-type=INSTANCE_TYPE]
   ```

   Provide the following values:

   * `INSTANCE_ID`: The permanent identifier for the instance.
   * `CLUSTER_ID`: The permanent identifier for the cluster.
   * `CLUSTER_ZONE`: The [zone](https://cloud.google.com/bigtable/docs/locations) where the cluster runs.

     If you plan to use [replication](https://cloud.google.com/bigtable/docs/replication-overview) within a single region, make sure Cloud Bigtable is available in at least one other zone in that region. [View the zone list](https://cloud.google.com/bigtable/docs/locations).

   * `DISPLAY_NAME`: A human-readable name that identifies the instance in the GCP Console.

   The command accepts the following optional flags:

   * `--cluster-num-nodes=CLUSTER_NUM_NODES`: The number of nodes in the cluster. Clusters in a production instance must have 3 or more nodes. The default value is `3`. If you aren't sure how many nodes you need, use the default. You can add more nodes later. [Learn more](https://cloud.google.com/bigtable/docs/instances-clusters-nodes#nodes).

     Do not use this flag for development instances.

   * `--cluster-storage-type=CLUSTER_STORAGE_TYPE`: The type of storage to use for the cluster. Each cluster in an instance must use the same storage type. Accepts the values `SSD` and `HDD`. The default value is `SSD`.

     In most cases, the default value is best. This choice is permanent. [Learn more](https://cloud.google.com/bigtable/docs/choosing-ssd-hdd).

   * `--instance-type=INSTANCE_TYPE`: The type of instance to create. Accepts one of the following values:
     * `PRODUCTION` \(default\): A high-availability, full-powered instance. This choice is permanent. [Learn more](https://cloud.google.com/bigtable/docs/instances-clusters-nodes#instances).
     * `DEVELOPMENT`: A low-cost instance for development and testing, with limited performance and no SLA. You can upgrade to a production instance later. [Learn more](https://cloud.google.com/bigtable/docs/instances-clusters-nodes#instances).

2. To enable replication for a production instance, use the [`bigtable clusters create` command](https://cloud.google.com/sdk/gcloud/reference/bigtable/clusters/create) to add a cluster:

   ```text
   gcloud bigtable clusters create CLUSTER_ID \
       --instance=INSTANCE_ID \
       --zone=ZONE \
       [--num-nodes=NUM_NODES] \
       [--storage-type=STORAGE_TYPE]
   ```

   Provide the following values:

   * `CLUSTER_ID`: The permanent identifier for the cluster.
   * `INSTANCE_ID`: The permanent identifier for the instance you just created.
   * `ZONE`: The [zone](https://cloud.google.com/bigtable/docs/locations) where the cluster runs.

     An instance's clusters must be in unique zones. You can create an additional cluster in any zone where Cloud Bigtable is available. For example, if the first cluster is in `us-east1-b`, you can choose a different zone in the same region, such as `us-east1-c`, or a zone in a separate region, such as `europe-west2-a`.

   The command accepts the following optional flags:

   * `--num-nodes=NUM_NODES`: The number of nodes in the cluster. Clusters in a production instance must have 3 or more nodes.

     In many cases, each cluster in an instance should have the same number of nodes, but there are exceptions. [Learn about nodes and replication](https://cloud.google.com/bigtable/docs/instances-clusters-nodes#nodes-replication).

   * `--storage-type=STORAGE_TYPE`: The type of storage to use for the cluster. Each cluster in an instance must use the same storage type. Accepts the values `SSD` and `HDD`. The default value is `SSD`.

