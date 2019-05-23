---
description: Manage Google Cloud Functions.
---

# gcloud functions

`gcloud functions` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:

* [`event-types`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/event-types)`(BETA)` List types of events that can be a trigger for a Google Cloud Function.
* [`logs`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/logs)`(BETA)` Display log entries produced by Google Cloud Functions.
* [`regions`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/regions)`(BETA)` List regions available to Google Cloud Functions.

`COMMAND` is one of the following:

* [`call`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/call)`(BETA)` Trigger execution of a Google Cloud Function.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/delete)`(BETA)` Delete a Google Cloud Function.
* [`deploy`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/deploy)`(BETA)` Create or update a Google Cloud Function.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/describe)`(BETA)` Display details of a Google Cloud Function.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/beta/functions/list)`(BETA)` List Google Cloud Functions.

```text
gcloud functions deploy $FUNCTION_NAME \
    --entry-point=imageParser --runtime=nodejs6 --source=$SOURCE_LOCAL_FOLDER \
    --stage-bucket=$PRIVATE_ASSETS \
    --trigger-resource=$PUB_SUB_TOPIC \
    --trigger-event="google.pubsub.topic.publish" \
    --project=$PROJECT_NAME \
    --region=$PROJECT_REGION \
    --set-env-vars=BIGTABLE_INSTANCE_ID=$BIGTABLE_INSTANCE_ID,BIGTABLE_TABLE_ID=$BIGTABLE_TABLE_ID,CLOUD_STORAGE_BUCKET=$PUBLIC_ASSETS
```



To call a function giving it hello world in message field of its event argument \(depending on your environment you might need to escape characters in --data flag value differently\):

```text
  $ gcloud beta functions call helloWorld \
    --data '{"message": "Hello World!"}'
```

