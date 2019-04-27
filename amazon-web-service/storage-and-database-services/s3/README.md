---
description: Simple Storage Service
---

# S3

As AWS's main storage service, S3 can serve many purposes including: 

* Bulk static object storage 
* Various storage classes to optimize cost vs. needed object availability/durability 
* Object versioning 
* Access restrictions via S3 bucket policies/permissions 
* Object management via lifecycle policies
* Hosting static files and websites Origin for CloudFront CDN 
* File shares and backup/archiving for hybrid networks \(via AWS Storage Gateway\)

### Important S3 Facts: 

* Objects stay within an AWS region and are synced across all AZ’s for extremely high availability and durability 
* You should always create an S3 bucket in a region that makes sense to it's purpose: Serving content to customers and Sharing Data with EC2

### S3 Read Consistency Rules: 

* ALL regions now support read-after-write consistency for PUTS of new objects into S3: Object can be immediately available after “putting” an object in S3 
* All regions use eventual consistency for PUTS overwriting existing objects and DELETES of objects

### S3 Errors \(S3 errors are generally handled with HTTP responses\) : 

* 404 Not Found 
* 403 Forbidden
* 400 Bad request 
* 500 Server Error Other Errors - [https://docs.aws.amazon.com/AmazonS3/latest/API/ErrorResponses.html](https://docs.aws.amazon.com/AmazonS3/latest/API/ErrorResponses.html)

## S3 Buckets

* Buckets are the main storage container of S3, and contain a grouping of information and have sub name spaces that are similar to folders \(but yet are called folders\) 
* Tags can be used to organize buckets \(i.e., tag based on an application the bucket belongs to\) 
* When creating a bucket, you can choose what region AWS will store your bucket's objects, this allows you to: 
  * Optimize latency 
  * Minimize costs 
  * Address regulatory requirements 
* S3 objects stay within a region unless explicitly transferred

### Bucket Naming Conventions - All S3 Buckets

* Must have a unique name across ALL of AWS 
* Must comply with DNS naming conventions 
* Minimum of 3 characters and a maximum of 63 characters long 
* Can only contain lowercase letters, numbers, periods, and hyphens 
* Must start with a letter or number NOT a period/hyphen 
* Periods and hyphens cannot follow each other \(linuxacademy-.com\) 
* Must not be in an IP address format \(e.g. 10.2.1.2\)

### Bucket Limitations: 

* Only 100 buckets can be created in an AWS account at a time 
* Bucket ownership cannot be transferred once a bucket is created 
* Can hold unlimited objects

## S3 Objects:

* Objects are static files and metadata information: 
  * Files are uploaded by the user 
  * AWS Metadata is applied to the object such as storage type, encryption settings, and permissions
* Each object must be assigned a storage type, which determines the object's availability, durability, and cost 
* By default, all objects are private 
* Objects can: 
  * Be as small as 0 bytes and as large as 5 TB 
  * Have multiple versions \(if versioning is enabled\) 
  * Be made publicly available via a URL 
  * Automatically switch to a different storage class or delete an object \(via lifecycle policies\) 
  * Encrypted 
  * Organized into "sub-name" spaces called folders

### Object Encryption: 

* SSE \(Server Side Encryption\): 
  * S3 can encrypt the object before saving it on the partitions in the data centers and decrypt it when it is downloaded 
  * AES-256
* Or you can use your own encryption keys: 
  * Considered client side encryption where you encrypt the data before upload

## S3 Folders:

* For simplicity, S3 supports the concept of "folders" 
* Folders are only used as a means of grouping objects 
* Amazon S3 creates folders by using key-name prefixes for objects 

#### Amazon S3 has a flat structure; there is no hierarchy like you would see in a typical file system.

## S3 Event Notifications:

* S3 **event notifications** allow you to setup automated communication between S3 and other AWS services when a selected event occurs in an S3 bucket
* Common event notification triggers include: 
  * RRSObjectLost \(Used for automating the recreation of lost RRS objects\) 
  * ObjectCreated \(for all or the following specific APIs called\): Put, Post, Copy, CompleteMultiPartUpload
* Event notifications can be sent to the following AWS services: SNS, Lambda, SQS Queue

