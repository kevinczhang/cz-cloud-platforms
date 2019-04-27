# Local and Global Secondary Indexes

## DynamoDB Secondary Indexes

* Indexes allow efficient queries of non-primary key attributes 
* Every secondary index is associated with only one table 
* Tables can have multiple secondary indexes 
* DynamoDB automatically maintains secondary indexes - when the base table is updated, so are the indexes

![](../../../.gitbook/assets/image%20%2838%29.png)

![](../../../.gitbook/assets/image%20%2821%29.png)

## DynamoDB Local Secondary Indexes \(LSIs\) 

Gives you a choice of sort keys for DynamoDB tables LSI Primary Keys are composite keys \(partition and sort key\)

![](../../../.gitbook/assets/image.png)

## DynamoDB Global Secondary Indexes \(GSIs\):

Each Global Secondary Index acts as another way to query the information using a different partition and different sort key

![](../../../.gitbook/assets/image%20%2836%29.png)

