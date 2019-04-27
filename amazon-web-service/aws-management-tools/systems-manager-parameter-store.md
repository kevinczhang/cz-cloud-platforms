# Systems Manager Parameter Store

Parameter Store provides a secure way to store configuration information and sensitive secrets: 

* You can use the service to store a variety of string values like: Passwords, Database strings, API keys, License codes.
* These values can be stored encrypted or as plaintext

### Benefits 

Parameter store gives you a variety of important benefits: 

* It provides a secure, scalable, and hosted secrets management service 
* It allows you to separate your sensitive data from source control 
* You can store parameters in hierarchies and track versions for easier organization 
* You can use these parameters across a variety of AWS services 
* You can audit, tag, and secure parameters using exisiting AWS services and tools

## Parameter Store API Actions

API actions related to Parameter Store will usually be taken through the AWS Console, AWS SDKs, or the AWS CLI. However, all those tools are rooted in AWS API actions. It's also important to note that Parameter Store actions are all underneath the AWS Systems Manager \(SSM\) umbrella.

Common API Actions: 

* **PutParameter** - Adds a parameter to Parameter Store 
  * Either a String, StringList, or SecureString 
  * A SecureString is a KMS-encrypted string that SSM can decrypt for you by using KMS 
* **GetParameter** - Gets a parameter from SSM: Can return the parameter value either encrypted or decrypted 
* **DeleteParameter** - Deletes a parameter from SSM

Other SSM API Actions - [https://docs.aws.amazon.com/systems-manager/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/systems-manager/latest/APIReference/Welcome.html)

