---
description: >-
  The gcloud container clusters command group lets you deploy and teardown
  Google Kubernetes Engine clusters.
---

# gcloud container clusters

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

