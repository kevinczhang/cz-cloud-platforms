# Access control

You can control who has access to your Cloud Storage buckets and objects as well as what level of access they have.

1. [Cloud Identity and Access Management \(Cloud IAM\) permissions](https://cloud.google.com/storage/docs/access-control/iam): Grant access to buckets as well as bulk access to a bucket's objects. Cloud IAM permissions give you broad control over your projects and buckets, but not fine-grained control over individual objects.
2. [Access Control Lists \(ACLs\)](https://cloud.google.com/storage/docs/access-control/lists): Grant read or write access to users for individual buckets or objects. 
3. [Signed URLs \(query string authentication\)](https://cloud.google.com/storage/docs/access-control/signed-urls): Give time-limited read or write access to an object through a URL you generate. 
4. [Signed Policy Documents](https://cloud.google.com/storage/docs/xml-api/post-object#policydocument): Specify what can be uploaded to a bucket. 
5. [Firebase Security Rules](https://firebase.google.com/docs/storage/security): Provide granular, attribute-based access control to mobile and web apps using the [Firebase SDKs for Cloud Storage](https://firebase.google.com/docs/storage). 

## 

####  <a id="three-object_bucket"></a>

