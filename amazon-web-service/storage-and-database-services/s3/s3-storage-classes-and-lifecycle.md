# S3 Storage Classes and lifecycle

## S3 Storage Classes

A storage class represents the "classification" assigned to each Object in S3 

| Storage class | Designed for | Availability Zones | Min storage duration |
| :--- | :--- | :--- | :--- |
| Standard | Frequently accessed data | ≥ 3 | - |
| Intelligent-Tiering | Long-lived data with changing or unknown access patterns | ≥ 3 | 30 days |
| Standard-IA | Long-lived, infrequently accessed data | ≥ 3 | 30 days |
| One Zone-IA | Long-lived, infrequently accessed, non-critical data | ≥ 1 | 30 days |
| Glacier | Archive data with retrieval times ranging from minutes to hours | ≥ 3 | 90 days |
| Glacier Deep Archive | Archive data that rarely, if ever, needs to be accessed with retrieval times in hours | ≥ 3 | 180 days |
| Reduced Redundancy \(Not recommended\) | Frequently accessed, non-critical data | ≥ 3 | - |

## Lifecycle Policies:

An object lifecycle policy is a set of rules that automate the migration of an object's storage class to a different storage class, or deletes it, based on specified time intervals:

* By default, lifecycle policies are disabled on a bucket/object 
* Are customizable to meet your company's data retention policies 
* Great for automating the management of object storage and to be more cost efficient 
* Can be used with versioning to create a great archiving and backup solution in S3: 
  * Send non-current versions to Amazon Glacier after X days 
  * Permenantly delete object versions Y days after they become non-current 
  * Separate policies for current and non-current versions

#### Example: 

* I have a work file that I am going to access every day for the next 30 days 
* After 30 days, I may only need to access that file once a week for the 60 next days 
* After which \(90 days total\) I will probably never access the file again but want to keep it just in case

![](../../../.gitbook/assets/image%20%288%29.png)



