---
description: Create or update a Google Cloud Function.
---

# gcloud functions deploy

`gcloud functions deploy` \([`NAME`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#NAME) : [`--region`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--region)=`REGION`\) \[[`--entry-point`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--entry-point)=`ENTRY_POINT`\]\[[`--ignore-file`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--ignore-file)=`IGNORE_FILE`\] \[[`--memory`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--memory)=`MEMORY`\] \[[`--retry`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--retry)\] \[[`--runtime`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--runtime)=`RUNTIME`\]\[[`--service-account`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--service-account)=`SERVICE_ACCOUNT`\] \[[`--source`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--source)=`SOURCE`\] \[[`--stage-bucket`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--stage-bucket)=`STAGE_BUCKET`\]\[[`--timeout`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--timeout)=`TIMEOUT`\] \[[`--update-labels`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--update-labels)=\[`KEY`=`VALUE`,…\]\] \[[`--clear-env-vars`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--clear-env-vars)    \| [`--env-vars-file`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--env-vars-file)=`FILE_PATH`     \| [`--set-env-vars`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--set-env-vars)=\[`KEY`=`VALUE`,…\]    \| [`--remove-env-vars`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--remove-env-vars)=\[`KEY`,…\] [`--update-env-vars`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--update-env-vars)=\[`KEY`=`VALUE`,…\]\] \[[`--clear-labels`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--clear-labels)    \| [`--remove-labels`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--remove-labels)=\[`KEY`,…\]\] \[[`--trigger-bucket`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--trigger-bucket)=`TRIGGER_BUCKET`     \| [`--trigger-http`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--trigger-http)    \| [`--trigger-topic`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--trigger-topic)=`TRIGGER_TOPIC`    \| [`--trigger-event`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--trigger-event)=`EVENT_TYPE` [`--trigger-resource`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#--trigger-resource)=`RESOURCE`\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/functions/deploy#GCLOUD-WIDE-FLAGS) `…`\]

```text
gcloud functions deploy $FUNCTION_NAME \
    --entry-point=imageParser 
    --runtime=nodejs6 
    --source=$SOURCE_LOCAL_FOLDER \
    --stage-bucket=$PRIVATE_ASSETS \
    --trigger-resource=$PUB_SUB_TOPIC \
    --trigger-event="google.pubsub.topic.publish" \
    --project=$PROJECT_NAME \
    --region=$PROJECT_REGION \
    --set-env-vars=BIGTABLE_INSTANCE_ID=$BIGTABLE_INSTANCE_ID,BIGTABLE_TABLE_ID=$BIGTABLE_TABLE_ID,CLOUD_STORAGE_BUCKET=$PUBLIC_ASSETS
```



