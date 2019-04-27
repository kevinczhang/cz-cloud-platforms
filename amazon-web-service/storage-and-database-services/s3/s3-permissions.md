# S3 Permissions

All buckets and objects are private by default - only the resource owner has access The resource owner can grant access to the resource \(bucket/objects\) through S3 resource based policies OR access can be granted through a traditional IAM policy There are two kinds of resource-based policies for S3: Bucket policies S3 Access Control Lists \(ACLs\)

## S3 IAM Policies 

### IAM Policies are attached to Users, Groups, and Roles: 

* IAM policies are not attached to S3 buckets or objects 
* Cannot grant access to anonymous users 
* Written in JSON and attached to a IAM User, Group, or Role

```text
{
    "Version": "2008-10-17",
    "Statement": [
        {
            "Sid": "eb-ad78f54a-f239-4c90-adda-49e5f56cb51e",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::664223697780:role/aws-elasticbeanstalk-ec2-role"
            },
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::elasticbeanstalk-us-east-2-664223697780/resources/environments/logs/*"
        }
    ]
}
```

### Specifying S3 Resources 

It is possible to use more advanced methods of specifying S3 resources in a policy. Let's look at a few different ways we can do this: 

* Specify a specific bucket: arn:aws:s3:::yourbucket 
* Specify a specific object: arn:aws:s3:::yourbucket/key\_name 
* Specify all objects in yourbucket: arn:aws:s3:::yourbucket/ __
* _Specify all buckets: arn:aws:s3:::_ 
* Use variables inside the policy: arn:aws:s3:::companybucket/developers/${aws:username}/\*

## S3 Resource Based Policies 

### Bucket policies

* Are policies that are attached to the S3 bucket \(not the objects in the bucket or to an IAM role or user\) 
* The permissions in the policy are applied to all objects in the bucket unless the object was created by a user outside of the bucket owner's account 
* Can be used to grant access to IAM users or other AWS accounts 
* The policy specifies what actions are allowed or denied for a particular user of that bucket - such as: 
  * Granting access to an anonymous User 
  * Who can execute certain actions like PUT or DELETE 
  * Restricting access based off of an IP address \(generally used for CDN management\) 
* Written in JSON and attached to the bucket \(not attached to objects\)

### S3 Access Control Lists \(ACLs\)

* ACLs can be used with S3 buckets and S3 objects 
* ACLs can't deny permissions or grant conditional permissions 
* Object ACLs are used when you need to: 
  * Manage access to objects not owned by the bucket owner 
  * Manage permissions at the object level and permissions vary by object 
  * Allow external acconts to manage policies on S3 objects 
* Examples of common use-cases with Canned ACLs: public-read: allows sharing an S3 object with the public aws-exec-read: allows EC2 to get AMI bundles from S3 
* ACLs are written in XML

