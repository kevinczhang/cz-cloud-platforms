---
description: Manage billing accounts and associate them with projects.
---

# gcloud beta billing

 `gcloud beta billing` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/beta/billing/#GROUP) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/beta/billing/#GCLOUD-WIDE-FLAGS) `…`\]

 `GROUP` is one of the following:

* [`accounts`](https://cloud.google.com/sdk/gcloud/reference/beta/billing/accounts)`(BETA)` Manage billing accounts.
* [`projects`](https://cloud.google.com/sdk/gcloud/reference/beta/billing/projects)`(BETA)` Manage the billing account configuration of your projects.

 To list billing accounts associated with the current user, run:

```text
  $ gcloud beta billing accounts list
```

To link one of the billing accounts `0X0X0X-0X0X0X-0X0X0X` with a project `my-project`, run:

```text
  $ gcloud beta billing projects link my-project \
      --billing-account 0X0X0X-0X0X0X-0X0X0X
```



