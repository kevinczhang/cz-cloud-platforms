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

