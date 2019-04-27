# AWS IAM

IAM \(Identity & Access Management\) is where you manage your AWS users, groups, and roles - and their access to AWS accounts and services: IAM provides access and access permissions to AWS resources \(such as EC2, S3, & DynamoDB\) IAM is global to all AWS regions, creating a user account will apply to all the regions

The common use of IAM is to manage: 

* Users 
* Groups 
* Roles 
* IAM Access Policies 
* Api Keys 
* Specify a password policy as well as manage MFA requirements on a per user basis

By default, any new IAM user you create in an AWS account is created with NO access to any AWS services. This is a non-explicit deny rule set on all new IAM users.

For all users \(besides the root user\), permissions must be given that grant access to AWS services \(this is done through IAM Policies\).

When a new AWS root account is created, it is “best practice” to complete the tasks listed in IAM under “Security Status” - which include:

* Delete your root access keys 
* Activate MFA on your root account 
* Create individual IAM users 
* User groups to assign permissions 
* Apply an IAM password policy

Best practice is to login and do daily work as an IAM user - NOT as the root user. 

It is also best to always best to practice the "**Principal of Least Privilege**" when administering AWS accounts, users, groups, and roles.

