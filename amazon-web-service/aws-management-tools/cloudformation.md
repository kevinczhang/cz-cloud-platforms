# CloudFormation

CloudFormation is the pure embodiment of infrastructure as code: 

* You can describe your application's architecture in a CloudFormation template as either JSON or YAML 
* You can then use that template to deploy copies of that architecture to: Other AWS regions Other AWS accounts 
* **CloudFormation Stacks** are a collection of AWS resources you can manage together as one unit 
* **CloudFormation Stacks** defined by **CloudFormation templates**

### Benefits 

* Saves you time by not having to manually create duplicate architectures in other regions 
* Since your infrastructure is now code, you can version control your infrastructure 
* Allows for infrastructure rollbacks to previous versions if a new version has issues 
* Allows you to prepare for disaster recovery scenarios by having your infrastructure fully described in code

## CloudFormation Templates

CloudFormation templates are JSON or YAML text files that describe your AWS infrastructure. These templates can have several sections but only the Resources section is required: 

* **Format Version** - The AWS CloudFormation template version that the template conforms to 
* **Description** - A string that describes the template that must follow the format version 
* **Metadata** - Additional information about the template that can provide implementation details 
* **Parameters** - Values to pass to your template when you create or update a stack 
* **Mappings** - Match a provided key to a set of named values 
* **Conditions** - Statements that determine when resources are created or properties are defined using logical operators called condition intrinsic functions 
* **Transform** - An optional section used to integrate with the AWS Serverless Application Model \(AWS SAM\) 
* **Resources** - Specifies the resources to be created and their properties 
* _Outputs_ - Specifies output values that can be imported to other stacks, returned in the response, or viewed in the AWS CloudFormation console

## CloudFormation Resources

CloudFormation supports a variety of AWS resources. These resources are identified with **Resource type identifiers**: 

* Resource type identifiers follow the format of: AWS::aws-product-name::data-type-name 
* Some examples of common resource type identifiers include: 
  * AWS::EC2::Instance 
  * AWS::DynamoDB::Table 
  * AWS::IAM::Role

In addition to a resource type identifier, each CloudFormation resource also has its own **properties**. Properties for each type of resource vary depending on the resource. For example: 

* An AWS::EC2::Instance resource might have an **AvailabilityZone** or **InstanceType** property 
* An AWS::IAM::Role resource can have neither of those properties but might have a **ManagedPolicyArns** property

You can also use **Resource Attributes** to control additional relationships and behaviors of your resources. These include: 

* CreationPolicy - Used to delay stack creation when you want to confirm some other part of the stack is setup completely 
* DeletionPolicy - Can be used to optionally keep around certain resources, like S3 buckets, or backup resources, like EBS, with a snapshot before deleting it 
* DependsOn - Allows you to specify that certain resources will be dependent on other resources for their creation 
* Metadata - Allows you to add optional metadata to resources 
* UpdatePolicy - Allows you to specify how CloudFormation should update a small subset of AWS resources

## CloudFormation Stack

A CloudFormation stack is a group of AWS resources that you can manage together: 

* Stack resources are defined by the stack's AWS CloudFormation template 
* You can create, update, or delete a group of AWS resources by creating, updating, or deleting a corresponding stack 
* Conceptual examples of stacks: 
  * All the AWS resources required to run a web application, such as a web server, a database, and networking rules 
  * All the AWS resources required to run a serverless microservice, such as API Gateway methods, resources, and deployments as well as Lambda Functions and DynamoDB tables 
* Stack resources are treated as one single unit: 
  * Stacks resources must all be created/deleted successfully for the stack to be created or deleted 
  * If a Stack resource cannot be created, CloudFormation will roll back the stack and automatically delete any resources that were created

## CloudFormation Intrinsic Functions

CloudFormation syntax provides several built-in functions to help you manage your stacks. You can use these functions to assign values to different CloudFormation properties that are only available at or after runtime.

You can use Intrinsic Functions in: 

* Resource properties 
* Outputs 
* Metadata attributes 
* Update policy attributes 
* You can also use **conditional intrinsic functions** to conditionally create your CloudFormation resources

## Common Intrinsic Functions: 

* Fn::GetAtt - Returns the value of an attribute from a resource in your CloudFormation template: 
  * Frequently used to get things like the Name or ARN of other resources 
* Fn::Join - Appends values into a single value separated by a delimiter 
* Ref - Returns a value you can use to refer to the provided parameter or resource, for example: 
  * A Ref to an EC2 Instance would return the instance ID 
  * A Ref to a Lambda Function would return the function name

Other Intrinsic Functions - [https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html)

