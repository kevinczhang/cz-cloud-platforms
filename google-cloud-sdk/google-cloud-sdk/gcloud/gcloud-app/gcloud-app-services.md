---
description: >-
  This set of commands can be used to view and manage your existing App Engine
  services.
---

# gcloud app services

`gcloud app services` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/app/services/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/app/services/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`browse`](https://cloud.google.com/sdk/gcloud/reference/app/services/browse)Open the specified service\(s\) in a browser.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/app/services/delete)Delete services in the current project.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/app/services/describe)Display all data about an existing service.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/app/services/list)List your existing services.
* [`set-traffic`](https://cloud.google.com/sdk/gcloud/reference/app/services/set-traffic)Set traffic splitting settings.

To list your deployed services, run:

```text
  $ gcloud app services list
```

## set-traffic

To send all traffic to 'v2' of service 's1', run:

```text
  $ gcloud app services set-traffic s1 --splits v2=1
```

To split traffic evenly between 'v1' and 'v2' of service 's1', run:

```text
  $ gcloud app services set-traffic s1 --splits v2=.5,v1=.5
```

To split traffic across all services:

```text
  $ gcloud app services set-traffic --splits v2=.5,v1=.5
```

