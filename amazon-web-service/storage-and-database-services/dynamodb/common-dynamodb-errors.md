# Common DynamoDB Errors

## DynamoDB Errors

**ThrottlingException**: You might be trying to delete, create, or update tables too quickly.

**ProvisionedThroughputExceededException**: The throughput on the table is insufficinet to support the amount of read and write operations you're doing.

**ResourceNotFoundException**: The requested table does not exist, or is too early in the CREATING state.

**More Errors - AWS Documentation**: [https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/CommonErrors.html](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/CommonErrors.html)

## DynamoDB Limits: 

* Secondary Indexes 
* Provisioned Throughput 
* Number of DynamoDB tables 
* Items and Attributes 
* Specific API Limits

Details about limits: [https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Limits.html](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Limits.html)

