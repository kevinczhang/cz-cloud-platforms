---
description: gcloud app instances - view and manage your App Engine instances
---

# gcloud app instances

 `gcloud app instances` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/app/instances/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/app/instances/#GCLOUD-WIDE-FLAGS) `…`\]

 `COMMAND` is one of the following:

* [`delete`](https://cloud.google.com/sdk/gcloud/reference/app/instances/delete)Delete a specified instance.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/app/instances/describe)Display all data about an existing instance.
* [`disable-debug`](https://cloud.google.com/sdk/gcloud/reference/app/instances/disable-debug)Disable debug mode for an instance.
* [`enable-debug`](https://cloud.google.com/sdk/gcloud/reference/app/instances/enable-debug)Enable debug mode for an instance \(only works on the flexible environment\).[`list`](https://cloud.google.com/sdk/gcloud/reference/app/instances/list)List the instances affiliated with the current App Engine project.
* [`scp`](https://cloud.google.com/sdk/gcloud/reference/app/instances/scp)SCP from or to the VM of an App Engine Flexible instance.
* [`ssh`](https://cloud.google.com/sdk/gcloud/reference/app/instances/ssh)SSH into the VM of an App Engine Flexible instance.

 To delete instance i1 of service s1 and version v1, run:

```text
  $ gcloud app instances delete i1 --service=s1 --version=v1
```

 To show all data about instance i1 for service s1 and version v1, run:

```text
  $ gcloud app instances describe --service=s1 --version=v1 i1
```

 To list all App Engine instances, run:

```text
  $ gcloud app instances list
```

To list all App Engine instances for a given service, run:

```text
  $ gcloud app instances list -s myservice
```

To list all App Engine instances for a given version, run:

```text
  $ gcloud app instances list -v v1
```

