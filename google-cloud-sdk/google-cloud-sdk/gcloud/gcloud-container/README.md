---
description: >-
  The gcloud container command group lets you create and manage Google
  Kubernetes Engine containers and clusters.
---

# gcloud container

`gcloud container` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/container/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/container/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/container/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:

* [`clusters`](https://cloud.google.com/sdk/gcloud/reference/container/clusters)Deploy and teardown Google Kubernetes Engine clusters.
* [`images`](https://cloud.google.com/sdk/gcloud/reference/container/images)List and manipulate Google Container Registry images.
* [`node-pools`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools)Create and delete operations for Google Kubernetes Engine node pools.
* [`operations`](https://cloud.google.com/sdk/gcloud/reference/container/operations)Get and list operations for Google Kubernetes Engine clusters.
* [`subnets`](https://cloud.google.com/sdk/gcloud/reference/container/subnets)Manage subnets to be used by Google Kubernetes Engine clusters.

`COMMAND` is one of the following:[`get-server-config`](https://cloud.google.com/sdk/gcloud/reference/container/get-server-config)Get Kubernetes Engine server config.

## gcloud container clusters

The gcloud container clusters command group lets you deploy and teardown Google Kubernetes Engine clusters.

`gcloud container clusters` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/#COMMAND) \[[`--region`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/#--region)=`REGION`     \| [`--zone`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/#--zone)=`ZONE`, [`-z`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/#-z) [`ZONE`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/#ZONE)\]\[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`create`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/create)Create a cluster for running containers.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/delete)Delete an existing cluster for running containers.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/describe)Describe an existing cluster for running containers.
* [`get-credentials`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/get-credentials)Fetch credentials for a running cluster.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/list)List existing clusters for running containers.
* [`resize`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize)Resizes an existing cluster for running containers.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/update)Update cluster settings for an existing container cluster.
* [`upgrade`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/upgrade)Upgrade the Kubernetes version of an existing container cluster.

```text
gcloud beta container clusters create $PRODUCT_CLUSTER_NAME \
    --project $PROJECT_NAME \
    --zone $PROJECT_ZONE \
    --no-enable-basic-auth \
    --cluster-version "1.11.7-gke.12" \
    --machine-type "n1-standard-1" \
    --image-type "COS" \
    --disk-type "pd-standard" \
    --disk-size "100" \
    --num-nodes "3" \
    --enable-cloud-logging \
    --enable-cloud-monitoring \
    --network $SERVICES_NETWORK \
    --subnetwork $PRODUCT_SUBNET \
    --addons HorizontalPodAutoscaling,HttpLoadBalancing,KubernetesDashboard \
    --enable-autoupgrade \
    --enable-autorepair \
    --service-account $SA_EMAIL
```

### gcloud container clusters resize - resizes an existing cluster for running containers

`gcloud container clusters resize` [`NAME`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#NAME) [`--num-nodes`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#--num-nodes)=`NUM_NODES`, [`--size`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#--size)=`NUM_NODES` \[[`--async`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#--async)\]\[[`--node-pool`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#--node-pool)=`NODE_POOL`\] \[[`--region`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#--region)=`REGION`     \| [`--zone`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#--zone)=`ZONE`, [`-z`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#-z) [`ZONE`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#ZONE)\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/resize#GCLOUD-WIDE-FLAGS) `…`\]

Resize an existing cluster to a provided size.

If you have multiple node pools, you must specify which node pool to resize by using the --node-pool flag. You are not required to use the flag if you have a single node pool.

When increasing the size of a container cluster, the new instances are created with the same configuration as the existing instances. Existing pods are not moved onto the new instances, but new pods \(such as those created by resizing a replication controller\) will be scheduled onto the new instances.

When decreasing a cluster, the nodes are drained. As a result, the pods running on these nodes are gracefully terminated. If your pods are being managed by a workload controller, the controller will attempt to reschedule them onto the remaining instances. If your pods are not managed by a workload controller, they will not be restarted. Note that when resizing down, instances running pods and instances without pods are not differentiated. Resize will pick instances to remove at random.

### gcloud container get-server-config - get Kubernetes Engine server config

`gcloud container get-server-config` \[[`--region`](https://cloud.google.com/sdk/gcloud/reference/container/get-server-config#--region)=`REGION`     \| [`--zone`](https://cloud.google.com/sdk/gcloud/reference/container/get-server-config#--zone)=`ZONE`, [`-z`](https://cloud.google.com/sdk/gcloud/reference/container/get-server-config#-z) [`ZONE`](https://cloud.google.com/sdk/gcloud/reference/container/get-server-config#ZONE)\]\[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/container/get-server-config#GCLOUD-WIDE-FLAGS) `…`\]

### gcloud container images - list and manipulate Google Container Registry images

`gcloud container images` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/container/images/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/container/images/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`add-tag`](https://cloud.google.com/sdk/gcloud/reference/container/images/add-tag)Adds tags to existing image.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/container/images/delete)Delete existing images.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/container/images/describe)Lists information about the specified image.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/container/images/list)List existing images.
* [`list-tags`](https://cloud.google.com/sdk/gcloud/reference/container/images/list-tags)List tags and digests for the specified image.
* [`untag`](https://cloud.google.com/sdk/gcloud/reference/container/images/untag)Remove existing image tags.

### gcloud container node-pools - create and delete operations for Google Kubernetes Engine node pools

`gcloud container node-pools` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/#COMMAND) \[[`--region`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/#--region)=`REGION`     \| [`--zone`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/#--zone)=`ZONE`, [`-z`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/#-z) [`ZONE`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/#ZONE)\]\[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`create`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/create)Create a node pool in a running cluster.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/delete)Delete an existing node pool in a running cluster.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/describe)Describe an existing node pool for a cluster.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/list)List existing node pools for a cluster.
* [`rollback`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/rollback)Rollback a node-pool upgrade.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/container/node-pools/update)Updates a node pool in a running cluster.

### gcloud container operations - get and list operations for Google Kubernetes Engine clusters

`COMMAND` is one of the following:

* [`describe`](https://cloud.google.com/sdk/gcloud/reference/container/operations/describe)Describe an operation.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/container/operations/list)List operations for container clusters.
* [`wait`](https://cloud.google.com/sdk/gcloud/reference/container/operations/wait)Poll an operation for completion.

### gcloud container subnets - manage subnets to be used by Google Kubernetes Engine clusters

`gcloud container subnets` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/container/subnets/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/container/subnets/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

[`list-usable`](https://cloud.google.com/sdk/gcloud/reference/container/subnets/list-usable)List subnets usable for cluster creation in a specific project.

