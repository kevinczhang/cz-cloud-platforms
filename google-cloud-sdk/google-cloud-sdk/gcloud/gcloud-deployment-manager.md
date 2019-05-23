---
description: >-
  The gcloud deployment-manager command group lets you manage the deployment of
  Google Cloud Platform resources using Google Cloud Deployment Manager.
---

# gcloud deployment-manager

Google Cloud Deployment Manager allows you to specify all the resources needed for your application in a declarative format using YAML. You can also use Python or Jinja2 templates to parameterize the configuration and allow reuse of common deployment paradigms such as a load balanced, auto-scaled instance group.

`gcloud deployment-manager` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/#GROUP) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:

* [`deployments`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/deployments)Commands for Deployment Manager deployments.
* [`manifests`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/manifests)Commands for Deployment Manager manifests.
* [`operations`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/operations)Commands for Deployment Manager operations.
* [`resources`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/resources)Commands for Deployment Manager resources.
* [`types`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/types)Commands for Deployment Manager types.

## gcloud deployment-manager deployments

Commands to create, update, delete, and examine deployments of resources.

`gcloud deployment-manager deployments` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/deployments/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/deployments/#GCLOUD-WIDE-FLAGS) `…`\]

To create a deployment, run:

```text
  $ gcloud deployment-manager deployments create my-deployment \
      --config config.yaml
```

To update a deployment, run:

```text
  $ gcloud deployment-manager deployments update my-deployment \
      --config new_config.yaml
```

To stop a deployment create or update in progress, run:

```text
  $ gcloud deployment-manager deployments stop my-deployment
```

To cancel a previewed create or update, run:

```text
  $ gcloud deployment-manager deployments cancel-preview my-deployment
```

To delete a deployment, run:

```text
  $ gcloud deployment-manager deployments delete my-deployment
```

To view the details of a deployment, run:

```text
  $ gcloud deployment-manager deployments describe my-deployment
```

To see the list of all deployments, run:

```text
  $ gcloud deployment-manager deployments list
```

