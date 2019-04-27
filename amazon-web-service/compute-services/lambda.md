# Lambda

AWS Lambda runs your code without you having to manage any server infrastructure. You just upload your Lambda Functions \(your code and dependencies\) and let AWS handle everything else required to run and scale your functions as needed.

* Lambda is a serverless computing platform: 
  * Serverless means that you can run code without provisioning or managing servers 
  * You pay only for the compute time you consume \(to the millisecond\) - you don't pay for any idle time 
  * By default, Lambda is highly available, fault-tolerant, scalable, elastic, and cost efficient 
* Lambda Functions or Lambda Function Packages are the core concept when programming with Lambda and consist of: 
  * Your application code 
  * Any application depedencies your code requires such as libraries, configuration, or other dependencies 
* Lambda easily integrates with many other AWS services including: 
  * CloudWatch Logs for monitoring 
  * API Gateway for exposing HTTP 
  * API endpoints backed by Lambda KMS to deal with encryption keys 
  * Many other services through the AWS SDKs and the IAM Role assigned to a Lambda Function on creation 
* Current supported languages include: Node.js, Java, C\#, Python, Go 
* Some Lambda use cases: 
  * Any event-driven task like S3 bucket changes or DynamoDB table updates 
  * Stream-processing and ETL processes 
  * IOT and mobile backends 
  * Web Application APIs

## Lambda Events: 

AWS Lambda Functions are triggered by events such as: 

* HTTP API requests through API Gateway 
* Cloudwatch scheduled events 
* S3 file uploads 
* DynamoDB Streams changes 
* Direct invocations using the CLI or SDKs 
* Many other event sources

## Programming Model 

All AWS Lambda language runtimes deal with similar concepts including: 

* Handler files and functions - the entry point for Lambda invocations 
* Events - the incoming data passed to a Lambda function when triggered 
* Contex - a way to get runtime information like time-remaining 
* Logging and Exceptions - are always handled through CloudWatch logs and functions communicate success and failure to AWS 
* Runtime-specific concepts - each runtime has a few differences and some have unique concepts like the Node.js callback which is used to return information back to the caller

### Invocation Types 

When invoking functions directly with the Lambda Invoke API action, you can pick an invocation type: 

* Synchronous - Wait for the return value and return it 
* Asynchronous - Don't wait for the return value - discard it

When triggered from an event, the type of invocation is determined by the service invoking the function.

## Lambda Function Configuration:

While Lambda requires significantly less configuration and management than traditional server infrastucture, it does still provide several options for customization: 

* The language runtime: Node.js v4.3.2/6.10.3, Java 8, Python 3.6/2.7, .NET Core 1.0.1/2.0, and Go 1.x 
* The handler: 
  * Each function has a handler file and function 
  * The format of the Lambda handler value is filename.functionname 
  * For example, a Python Lambda function might have a file called uptime\_check.py with a function inside called scan - The handler name would be uptime\_check.scan 
* Memory: 
  * 128 MB to 3008 MB \(in 64MB Increments\) 
  * CPU allocation scales with memory 
* Maximum execution duration: 15 minutes \(in 1 second increments\) 
* Permissions: 
  * IAM Roles grant the function permissions to take actions on other AWS resources 
  * Resource-based access control policies allow other services and external accounts to invoke or take other actions on a Lambda function 
* Environment Variables: 
  * Key-value pairs available at runtime for all functions 
  * Can be encrypted using KMS 
* AWS Virtual Private Cloud \(VPC\) - Grant your function access to VPC resources 
* Dead Letter Queues - Configure SQS or SNS to accept data from failed function executions 
* Concurrency - Specify the maximum number of concurrent invocations of your function 
* Tags - Key-value pairs to help you organize your functions

## Lambda Function Packages

Function packages, or "deployment packages", are zip packages of all the code and dependencies required by your Lambda function when it runs.

#### Function packages include: 

* Your handler file 
* Custom libraries or packages 
* Any other application code that integrates with your handler
*  Third-party packages from providers like npm or pip that your function requires 
* Specific examples: 
  * Python - pip install your libraries in the same directory as your function code 
  * Node.js - Include your node\_modules folder with the npm dependencies

## Lambda Versions and Aliases

Lambda provides you with two useful tools for managing your production function code: 

### Versions: 

* Lambda versions are distinct versions of your functions stored inside of AWS each with their own unique ARNs 
* Versions are either: 
  * The $LATEST version - literally just called $LATEST This is the only mutable \(changeable\) version 
  * A numbered version - like 1 or 2 
    * Numbered versions are assigned a number starting with one and each subsequent version is incremented by one 
    * Numbered versions are immutable 
* Because different versions have unique ARNs this allows you to effectively manage them for different environments like Production, Staging or Development 

### Aliases: 

* Lambda Aliases are like a pointer to a specific Lambda version 
* Using aliases you can invoke a function with the alias without having to know which version of the function is being referenced 
* Aliases have static ARNs but can point to any version of the same function 
* Aliases can also be used to split traffic between Lambda versions

### Benefits of Versions and Aliases

* Easier development workflow and management of stages 
* Avoid having to reconfigure event sources \(they can just point to a function alias\) 
* Rolling back to an earlier version becomes as easy as updating the alias 
* Using Alias traffic splitting between versions can also help test new versions in production

