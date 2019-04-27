# SQS

* SQS provides the ability to have hosted/highly available queues that can be be used to send and receive messages being sent between producers and consumers 
* This allows for the creation of **distributed/decoupled** application components 
* Messages between servers are retrieved through **polling**

### Two types of polling

* Long Polling \(1-20 seconds\): 
  * Allows the SQS service to wait until a message is available in a queue before sending a response 
  * Long polling reduces API requests \(over using short polling\) 
* Short Polling: 
  * SQS samples a subset of servers and returns messages from just those servers 
  * Will not return all possible messages in a poll 
  * Increases API requests \(over long polling\), which increases costs

### Other important SQS facts

* Each message can contain up to 256KB of text \(in any format\) 
* Amazon SQS offer two different types of queues: 
  * Standard Queues 
  * First-in-first-out \(FIFO\) Queue 
* SQS is also highly available and redundant 
* SQS can be PCI Compliant and can also encrypt message data using KMS

## SQS Producers

SQS Producers are any application, service, or other components that produce SQS messages and send them to an SQS queue.

#### Example Producers: 

* An application on an EC2 instance 
* AWS Lambda functions 
* ECS services 
* External AWS or non-AWS applications configured to send messages to SQS

## SQS Consumers

SQS Consumers are any application, service, or other components that process SQS messages. Consumers are also responsible for deleting messages from a queue.

#### Example Consumers: 

* AWS Lambda functions that process transaction information and send fulfillment emails 
* An ECS analytics service that processes SQS data and stores it in S3 for later analysis

## SQS Queue

SQS Queues are highly-reliable hosted message stores. There are two types of SQS queues:

### Standard Queues

* Support a 'nearly unlimited' number of messages per second 
* Support multiple producers and multiple consumers 
* Guarantee delivery of each message at least once with best effort ordering 
* Are used with applications that can tolerate duplicate messages 
* Support 120,000 In-Flight messages 

### First-In-First-Out \(FIFO\) Queues

* Support up to 3,000 messages per second with batching and 300 messages per second without batching \(you can ask AWS to increase these limits\) 
* Support multiple producers but only support multiple consumers through the use of Group IDs: 
  * Group IDs can be used to interleave multiple ordered message groups within a single FIFO queue 
  * Messages are proceessed in order with respect to the group but not always with respect to other groups 
* Are designed for applications where the order of operations and events is critical, or where duplicates can't be tolerated - **FIFO Queues garuntee that messages are sent and processed in order** 
* Support 20,000 In-Flight messages

### Queue Settings

* Dead-Letter Queues - Used to deal with malformed data from consumers 
* DelaySeconds - How long messages take to be added to the queue upon creation 
* VisibilityTimeout - How long messages are invisible after being received by a consumer

## SQS Resource-Based Access Control Policies

* Grant access to your SQS queues to another AWS account 
* The SQS AddPermission API automatically generates an access control policy to SQS 
* Grant access to some AWS services to publish to your SQS queue \(Many services like EC2 or AWS Lambda will use an IAM Role instead\) 
* Can use IAM Policies and Access Control policies at the same time

## SQS Polling

The action of receiving SQS messages from a queue is also called 'polling'. You can poll SQS queues with either short polling or long polling.

### Short Polling

* Short polling is the default method of retrieving data from an SQS queue 
* Short polling queries a subset of the SQS servers to determine if there are messages available for a response 
* Short polling occurs when the WaitTimeSeconds attribute is set to 0 for either the queue itself or the specific message when using the ReceiveMessage API
* If a message is assigned a WaitTimeSeconds greater than 0, then it will override the queue's WaitTimeSeconds 

### Long Polling 

* Occurs only when the queue or the message have a WaitTimeSeconds 
* Allows your consumers to wait for messages to become available in the queue 
* Generally cheaper because you are making fewer requests and fewer connections

## SQS Message

SQS messages are text information created by your application and sent to SQS.

### Message Characterstics and Limitations

SQS Messages can: 

* Be up to 256KB of text \(in any format\) 
* contain up to 10 metadata attributes \(outside of the message body\) 
* Be XML, JSON or unformatted text 
* Be retained in a queue for up to 14 days or as little as one minute 
* Be invisible in a queue for up to 12 hours 
* Be added to dead letter queues if consumers are unable to process them

### Important Message Components

* Body - The XML, JSON or unformatted text body of the message 
* ReceiptHandle - A message attribute that allows you to delete the message after receiving and processing it 
* MessageAttributes - Custom attributes you can set with your SQS message 
* VisibilityTimeout - The length of time that the queue will wait before making the message visible again after the message has been recieved \(to allow time for processing\) 
* DelaySeconds - The length of time that the queue will wait before initially placing the message in the queue

### Example Message Lifecycle: 

1. A producer sends a message to a queue and the message is redundantly distributed across SQS servers. 
2. When a consumer is ready, it polls the queue to receive the message from SQS. While the consumer processes the message, a queue-level or message-specific visibility timeout is applied to the message so it is not returned to subsequent polling until the timeout has expired. 
3. The consumer finishes processing the message and deletes it from the queue during the visibility timeout \(or else it would be processed again\).

## SQS API Actions

Like other AWS services, SQS has a variety of API actions you'll need to understand when working with it. Here are a subset of these actions put together in one example use case:

1. CreateQueue - You start by creating your first queue 
2. GetQueueUrl - You use this to return the URL you need for future actions 
3. SendMessage - Then you use a producer to send one or more messages into the queue 
4. ReceiveMessage - After that you start to receive messages with one or more consumers 
5. ChangeMessageVisibility - Those consumers sometimes need more time than the default Message Visibility so you increase the Message Visibility for the relevant messages 
6. DeleteMessage - The consumer finishes processing the message and deletes it from the queue

### SDK Benefits Over APIs

* Handles access credentials and signitures 
* Deals with automatic retry logic 
* Easier to program with 
* SDK Methods are updated and supported by AWS and the community

#### Other SQS API actions: [https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/Welcome.html) 

#### Common SQS Errors: [https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/CommonErrors.html](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/CommonErrors.html)

