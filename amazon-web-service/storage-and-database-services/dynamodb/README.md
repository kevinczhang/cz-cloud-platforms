# DynamoDB

Amazon DynamoDB is a managed NoSQL database service that provides fast performance and scalability. DynamoDB offloads things like the hardware provisioning, setup, configuration, replication, software patching, and cluster scaling.

## DynamoDB Key Features:

* Fully managed NoSQL database: 
  * AWS scales compute resources for you 
  * Mange data, not software/hardware 
  * Built-in monitoring 
  * Schemaless, key-value store 
* Consistent and fast performance: 
  * Data stored on fast SSDs 
  * Control throughput with read/write capacity 
  * Replicated across multiple AWS avilability zones 
  * DynamoDB Global Tables allow for replication across AWS regions 
* Easy to setup and communicate with: 
  * AWS Console or APIs 
  * CLI and SDKs 
  * Easily integrates with other AWS services 
  * DynamoDB Streams - Allows for other services to take action based on changes to DynamoDB items 
* Optional encryption at rest 
* Popular use cases include: IOT \(storing meta data\) Gaming \(storing session information, leaderboards\) Mobile \(Storing user profiles, personalization\)

## Core Concepts

### DynamoDB Partition Keys:

* Every DynamoDB table requires a partition key 
* The partition key of an item is also know as its hash attribute 
* Partition key attributes must be scalar \(they can only hold one value\) 
* DynamoDB uses partitions keys in an internal hash function to determine where the partition data will be stored \(see partitions\)

### DynamoDB Sort Keys:

* DynamoDB tables do not require a sort key 
* The sort key of an item is also know as its range attribute 
* Range key attributes must be scalar \(they can only hold one value\) 
* After DynamoDB uses the partition key to determine the partition data will be stored in \(see partitions\), the sort key is used to sort the data inside of that partition

### DynamoDB Primary Key:

The primary key uniquely identifies each item, so that no two items in a table can have the same key

#### There are two types of primary key: 

1. Simple Primary Key \(partition key only\)
   1. Made from one attribute that acts as the partition key 
   2. In this model, no two items can have the same partition key 
   3. Items in this kind of table must have a partition key
2. Composite Primary Key \(partition key and sort key\) 
   1. Key is made from two attributes; one acts as the partition key, the other as the sort key 
   2. Partition key determines the physical partition the item is stored in 
   3. Sort key determines the order for items with the same partition key 
   4. Items can have the same partition key OR the same sort key 
   5. Items must have a unique combination of partition key and sort key 
   6. Items are required to have both a partition key and a sort key

Primary key attributes must have the data type of string, number, or binary

### DynamoDB Attributes:

Attributes are the fundamental data elements of DynamoDB. They are similar to fields and columns in other databases.

Attribute Data Types: 

* Scalar Types - String, Number, Binary, Boolean, 
* Null Document Types - List, Map 
* Set - Number Sets, String Sets, Binary Sets

Example Attributes: 

MyScalarStringAttribute : "A String Value"

MyScalarNumberAttribute: 714887009

```text
MyDocumentAttribute : {
		"Street": "1500 Garfield Ave.",
		"City": "Seattle",
		"PostalCode": "98134"
}
```

## DynamoDB Partitions:

* DynamoDB stores data in partitions 
* Partitions are SSD allocations of storage for the table and automatically replicated across multiple AWS Availability Zones 
* Number of partitions is determined by the table's provisioned capacity and the storage size of exisiting partitions

![](../../../.gitbook/assets/image%20%287%29.png)

## DynamoDB Items:

Items are groups of attributes that are uniquely identifiable among all other items in a table.

Each item is one or more attributes and can be thought of as similar to rows in relational databases.

Example item from a Music table: 

```text
{       
    "Artist": "Anthony James",
    "SongTitle": "Learning For Dayz",
    "AlbumTitle": "A Few of My Favorite Things",
    "Genre": "Punk Rock",
    "Price": "1.99",
    "CriticRating": "8.1"
}
```

The names and values for Artist, SongTitle, AlbumTitle, Genre, Price, and CriticRating are all attributes that make up the item.



