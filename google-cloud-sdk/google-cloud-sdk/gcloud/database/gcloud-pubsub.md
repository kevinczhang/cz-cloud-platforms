# gcloud pubsub

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

