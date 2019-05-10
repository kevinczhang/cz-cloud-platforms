# IAM Definitions

## IAM Policies

A policy is a document that formally states one or more permissions. 

By default, an explicit deny always overrides and an explicit allow. This allows for the use of a "deny all" policy to quickly restrict ALL access that a user may have through multiple attached policies.

IAM provides pre-built policy templates to assign to users and groups, examples include: 

* **Administrator access**: Full access to ALL AWS resources. 
* **Power user access**: Admin Access except it does not allow user/group management. 
* **Read only access**: Only view AWS resources \(i.e. user can only view what is in an S3 bucket\).

You can also create custom IAM permission policies using the policy generator or written from scratch. 

More than one policy can be attached to a user or group at the same time. 

Policies cannot be directly attached to AWS resources \(such as an EC2 instance\).

```text
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:Get*",
                "s3:List*"
            ],
            "Resource": "*"
        }
    ]
}
```

## IAM Users

* When first created, by default an IAM User has a non-explicit “deny” for all AWS services - and does NOT have access to use them until a policy granting allow access has been applied to the user or to the group the user belongs to. 
* IAM Users receive unique access credentials so you do not \(and should not\) share with others. 
* User credentials should NEVER be stored or “passed” to an EC2 instance. 
* Users can have group and regular user policies apply to them - meaning a user can have multiple IAM policies applied to them at any given time. 
* By default, an explicit deny always overrides an explicit allow from attached IAM policies. 
* MFA can be configured on a per user basis for login and resource access/actions.

## IAM Groups

* Allow you to assign IAM permission policies to more than one user at a time.
* This ability allows for easier access management to AWS resources.

## IAM Roles

* **A role** is something that another entity can "assume", and in doing so acquires the specific permissions defined by the role. 
* In the context of this course, "entities" that can assume a role include AWS resources \(such as an EC2 instance\) OR a non-AWS account holder who may need temporary access to an AWS resource \(through a service like Active Directory\). 
* Roles must be used because policies cannot be directly attached to AWS services.

Other uses of roles: 

* Other users can assume a “role” for temporary access to AWS accounts and resources through having something like Active Directory or single sign-on service \(i.e Facebook, Google\) assume an "Identity Provider Access" role. 
* Create “cross account” access where a user from one account can assume a role with permissions in another account.

## IAM Security Token Service \(STS\):

* STS allows you to create temporary security credentials that grant trusted users access to your AWS resources. 
* These temporary credentials are for short-term use, and can be active for a few minutes to several hours. 
* Once expired, they can no longer be used to access your AWS resources. 
* When requested through an STS API call, credentials are returned with three components: **Security Token,** **An Access Key ID,** **A Secret Access key**.

#### STS Benefits:

* No distributing or embedding long-term AWS security credentials in an application. 
* Grant access to AWS resources without having to create an IAM identity for them. The basis for IAM roles and identity federation. 
* Since the credentials are temporary, you don't have to rotate or revoke them. You decide how long they are active for.

#### When to use STS:

* Identity Federation: 
  * Enterprise identity federation \(authenticate through your companies network\). STS Supports Security Assertion Markup Language \(SAML\), which allows for use of Microsoft Active Directory \(of your own solutions\). 
  * Web identity federation \(3rd party identity providers, i.e. Facebook, Google, Amazon\) 
* Roles for Cross-Account Access Used for organizations that have more than one AWS account. 
* Roles for Amazon EC2 \(and other AWS services\) Grant access an to application running on an EC2 instance to access other AWS services without having to imbed credentials.

### STS API Calls

* AssumeRole: Cross-Account Delegation and Federation Through a Custom Identity Broker.
* AssumeRoleWithWebIdentity: Federation Through a Web-based Identity Provider.
* AssumeRoleWithSAML: Federation Through an Enterprise Identity Provider Compatible with SAML 2.0.
* GetFederationToken: Federation Through a Custom Identity Broker.
* GetSessionToken: Temporary Credentials for Users in Untrusted Environments

## IAM API Keys:

API Access Keys are required to make programmatic calls to AWS from the: AWS Command Line Interface \(CLI\); Tools for Windows PowerShell; AWS SDKs; Direct HTTP calls using the APIs for individual AWS services.

Important API Access Key Facts: 

* API Keys are only available ONE time, when a new user is created OR when you reissue a new set of keys.
* AWS will NOT regenerate the same set of access keys. 
* In order for API credentials to work, they must be assocaited with a USER.
* Roles does not have API credentials.
* In the AWS console you can only see the Access Key ID - never the Secret Key ID 
* If you require new API credentials - you must deactivate the current set and generate new one. 
* NEVER create or store API keys on an EC2 instance.

## AWS Key Management Service \(KMS\):

KMS is a managed service to create and control the encryption keys used to encrypt your data.

### KMS Concepts: 

1. **Customer Master Keys** \(CMKs\): 
   1. CMKs are used to encrypt/decrypt up to 4KB of data, and are the primary resource in KMS 
   2. Typically, CKMs generate, encrypt, and decrypt data keys that you use outside of AWS KMS to encrypt your data 
   3. There are two types of CMKs: 
      1. **Customer-managed**: CMKs you create, enable/disable, rotate, and which manage the policies that allow access to use the CMK 
      2. **AWS-managed**: CMKs that are created, managed, and used by AWS services integrated with KMS \(these CMKs are named like this: aws/service-name e.g. aws/s3\) 
2. **Data Keys**: Encryption keys for encrypting large amounts of data or other data encryption keys. AWS CMKs can generate, encrypt, and decrypt data keys. KMS does not manage or store your data keys - you must use and manage them inside your application. KMS cannot use data keys to encrypt data for you.
3. **Envelope Encryption**: Plaintext data is encrypted with a data key. Data keys are encrypted with a key encryption key \(KEK\). A KEK may be encrypted by another KEK, but eventually there is a master key \(the KMS CMK in this case\) that decrypts one or more keys.

### KMS API Actions 

* Encrypt - Encrypt plaintext using a CMK 
* GenerateDataKey - Uses a CMK to return a plaintext and ciphertext version of a data encryption key 
* Decrypt - Decrypts ciphertext that was encrypted with the Encrypt, GenerateDataKey or GenerateDataKeyWithoutPlaintext API Actions

More Information - [https://docs.aws.amazon.com/kms/latest/developerguide/overview.html](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) API Reference - [https://docs.aws.amazon.com/kms/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/kms/latest/APIReference/Welcome.html)

## Amazon Cognito:

Amazon Cognito is **not underneath the IAM service umbrella**. But it can be seen as a superset of the functionality of web identity federation, so it's important to mention it while we're still talking about identity.

Amazon Cognito Identity: 

* Create unique identities for application users 
* Authenticate identities with your own auth process or via providers like Google and Facebook 
* Cognito supports unauthenticated identities: Lets users sign up after they use an application 
* Save mobile user data 
* Use credentials obtained to sync data with Cognito Sync

Amazon Cognito Sync: 

* Sync user data across mobile devices and the web 
* Client libraries cache data locally



