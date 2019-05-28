---
description: Create and manage Google Cloud Dataproc clusters.
---

# gcloud dataproc clusters

`gcloud dataproc clusters` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/#COMMAND) \[[`--region`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/#--region)=`REGION`\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`create`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/create)Create a cluster.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/delete)Delete a cluster.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/describe)View the details of a cluster.
* [`diagnose`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/diagnose)Run a detailed diagnostic on a cluster.
* [`get-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/get-iam-policy)Get IAM policy for a cluster.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/list)View a list of clusters in a project.
* [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/set-iam-policy)Set IAM policy for a cluster.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/dataproc/clusters/update)Update labels and/or the number of worker nodes in a cluster.

To create a cluster, run:

```text
  $ gcloud dataproc clusters create my_cluster
```

To resize a cluster, run:

```text
  $ gcloud dataproc clusters update my_cluster --num_workers 5
```

To delete a cluster, run:

```text
  $ gcloud dataproc clusters delete my_cluster
```

To view the details of a cluster, run:

```text
  $ gcloud dataproc clusters describe my_cluster
```

To see the list of all clusters, run:

```text
  $ gcloud dataproc clusters list
```

