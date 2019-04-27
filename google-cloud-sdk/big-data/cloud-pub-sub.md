# Cloud Pub/Sub

Cloud Pub/Sub brings the flexibility and reliability of enterprise message-oriented middleware to the cloud. At the same time, Cloud Pub/Sub is a scalable, durable event ingestion and delivery system that serves as a foundation for modern stream analytics pipelines.

## Creation

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

## Core concepts

* **Topic**: A named resource to which messages are sent by publishers. 
* **Subscription**: A named resource representing the stream of messages from a single, specific topic, to be delivered to the subscribing application. 
* **Message**: The combination of data and \(optional\) attributes that a publisher sends to a topic and is eventually delivered to subscribers. 
* **Message attribute**: A key-value pair that a publisher can define for a message.

## Cloud Pub/Sub message flow

1. A [_publisher_ application](https://cloud.google.com/pubsub/docs/overview#endpoints) creates a _topic_ in the Cloud Pub/Sub service and sends _messages_ to the topic. A message contains a payload and optional _attributes_ that describe the payload content. 
2. Messages are persisted in a _message store_ until they are delivered and acknowledged by subscribers.
3. Cloud Pub/Sub forwards messages from a topic to all of its subscriptions, individually. Each subscription receives messages either by Cloud Pub/Sub _pushing_ them to the subscriber's chosen endpoint, or by the subscriber _pulling_ them from the service.
4. The subscriber receives pending messages from its subscription and acknowledges each one to the Cloud Pub/Sub service. 
5. When a message is acknowledged by the subscriber, it is removed from the subscription's message queue.

 

