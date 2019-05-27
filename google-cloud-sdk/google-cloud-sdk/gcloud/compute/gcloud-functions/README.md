---
description: Manage Google Cloud Functions.
---

# gcloud functions

`gcloud functions` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:

* [`event-types`](https://cloud.google.com/sdk/gcloud/reference/functions/event-types)List types of events that can be a trigger for a Google Cloud Function.
* [`logs`](https://cloud.google.com/sdk/gcloud/reference/functions/logs)Display log entries produced by Google Cloud Functions.
* [`regions`](https://cloud.google.com/sdk/gcloud/reference/functions/regions)List regions available to Google Cloud Functions.

`COMMAND` is one of the following:

* [`call`](https://cloud.google.com/sdk/gcloud/reference/functions/call)Trigger execution of a Google Cloud Function.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/functions/delete)Delete a Google Cloud Function.
* [`deploy`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy)Create or update a Google Cloud Function.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/functions/describe)Display details of a Google Cloud Function.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/functions/list)List Google Cloud Functions.

## gcloud functions call

To call a function giving it hello world in message field of its event argument \(depending on your environment you might need to escape characters in --data flag value differently\):

```text
  $ gcloud beta functions call helloWorld \
    --data '{"message": "Hello World!"}'
```





