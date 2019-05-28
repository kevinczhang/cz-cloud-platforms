---
description: 'Manage Cloud Pub/Sub topics, subscriptions, and snapshots.'
---

# gcloud pubsub

`gcloud pubsub` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/pubsub/#GROUP) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/pubsub/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:

* [`snapshots`](https://cloud.google.com/sdk/gcloud/reference/pubsub/snapshots)Manage Cloud Pub/Sub snapshots.
* [`subscriptions`](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions)Manage Cloud Pub/Sub subscriptions.
* [`topics`](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics)Manage Cloud Pub/Sub topics.

This self-contained example, meant to run in bash or the Cloud Shell, shows the steps required:

1. Create a topic.
2. Subscribe to the topic.
3. Publish a message to the topic.
4. Receive the message.

```text
gcloud init
gcloud pubsub topics create my-topic
gcloud pubsub subscriptions create --topic my-topic my-sub
gcloud pubsub topics publish my-topic --message "hello"
gcloud pubsub subscriptions pull --auto-ack my-sub
```

