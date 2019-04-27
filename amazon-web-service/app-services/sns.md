---
description: Simple notification service
---

# SNS

* SNS is a Pub-sub service for messaing 
* SNS coordinates and manages the sending and delivery of messages to specific endpoints 
* We are able to use SNS to receive notifications when events occur in our AWS Environment 
* SNS is integrated into many AWS services, so it is very easy to setup notifications based on events that occur in those services 
* With CloudWatch and SNS, a full-environment monitoring solution can be created that notifies administrators of alerts, capacity issues, downtime, changes in the environment, and more! 
* This service can also be used for publishing IOS/Android app notifications and creating automation based off of notifications

**SNS Components**: Topic, Subscription, Publisher

**SNS Benefits**: 

* Scalable and highly reliable 
* Usable through the AWS Console, APIs, CLI, and multiple SDKs

## SNS Topic:

* Topics are the group of subscriptions that you send a message to 
* Topics require unique names limited to 256 characters 
* Topic names allow alphanumeric characters plus hyphens and underscores 
* Topics and messages are stored redundantly across multiple servers and data centers

## SNS Subscriber:

* An endpoint that a message is sent to 
* Available endpoints include: 
  * HTTP 
  * HTTPS 
  * Email 
  * Email-JSON 
  * SQS 
  * Application, Mobile APP notifications \(IOS/Android/Amazon/Microsoft\) 
  * Lambda 
  * SMS \(cellular text message\)

## SNS Publisher:

* The "entity" that triggers the sending of a message 
* Examples include: 
  * AWS CLI 
  * AWS SDKs \(e.g. Boto3\) 
  * AWS services: 
    * S3 Events 
    * Cloudwatch Alarms 
    * Using Lambda to publish to SNS

## SNS Access Control Policies:

* Grant access to your SNS topics to another AWS account: 
  * Amazon SNS API - AddPermission: 
    * Topic, AWS Account ID\(s\), Actions, Label 
    * Automatically generate an access control policy to SNS 
* Grant access to some AWS services to publish to your SNS topic \(Many services like EC2 or AWS Lambda will use an IAM Role instead\) 
* Can use IAM Policies and Access Control policies at the same time

## SNS Messages

* Typically JSON formatted key-value pairs 
* Allows developers to grab message data and parse it 
* POSTs to HTTP/S endpoints with specific headers: Headers allow verification of message authenticity 
* Message content depends on the subscriber

### Message Body 

* Message - The message value specified when the notification was published 
* MessageId - A Universally Unique Identifier \(UUID\). The same id must be reused for retries 
* Signature - Base64-encoded "SHA1withRSA" signature of the Message, MessageId, Subject, Type, Timestamp, and TopicArn values 
* SignatureVersion - Version of Amazon SNS Signature used 
* SigningCertURL - The URL to the certificate used to sign the message 
* Subject - An optional subject parameter 
* Timestamp - The GMT time when the notification was published 
* TopicArn - The ARN for the topic that this message was published to 
* Type - The type of message \(Notifications are type Notification\) 
* UnsubscribeURL - A URL you can use to unsubscribe from the SNS topic

### Message Attributes 

* Useful for SQS and moible push notifications 
* Sent along with the message 
* Each message attribute needs a Name, Type, and Value

## SNS Mobile Push

* Ability to send notifications directly to apps on mobile devices 
* Notifications sent to these endpoints can appear as message alerts, badge updates, and sound alerts

### Mobile Push Notification Services 

Different providers allow you to send notifications to different devices: 

* Amazon Device Messaging \(ADM\) 
* Apple Push Notification Service \(APNS\) 
* Baidu Cloud Push 
* Google Cloud Messaging for Andriod 
* Microsoft Push Notification Service for Windows Phone 
* Windows Push Notification Services

MPNS Process SNS requires 'device tokens' or 'registrations IDs' \(depending on the platform\) to send messages to devices.

## SNS API Actions

Common Actions: Create Topic, Publish, Subscribe, Unsubscribe

Other API actions [https://docs.aws.amazon.com/sns/latest/api/API\_Operations.html](https://docs.aws.amazon.com/sns/latest/api/API_Operations.html)

Common SNS Errors [https://docs.aws.amazon.com/sns/latest/api/CommonErrors.html](https://docs.aws.amazon.com/sns/latest/api/CommonErrors.html)

