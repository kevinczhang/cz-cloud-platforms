---
description: >-
  GCP offers Cloud IAM, which lets you manage access control by defining who
  (identity) has what access (role) for which resource.
---

# Cloud IAM

## Overview

![Cloud IAM](../../.gitbook/assets/image%20%2819%29.png)

In Cloud IAM, you grant access to **members**. Members can be of the following types:

* Google account \(A Google account represents a developer, an administrator, or any other person who interacts with GCP.\)
* Service account \(A service account is an account that belongs to your application instead of an individual end user. When you run code that is hosted on GCP, you specify the account that the code should run as.\)
* Google group \(A Google group is a named collection of Google accounts and service accounts. Every group has a unique email address that is associated with the group. \)
* G Suite domain \( A G Suite domain represents a virtual group of all the Google accounts that have been created in an organization's [G Suite](https://gsuite.google.com/) account. \)
* Cloud Identity domain \(A Cloud Identity domain is like a G Suite domain because it represents a virtual group of all Google accounts in an organization.\)

#### allAuthenticatedUsers <a id="allauthenticatedusers"></a>

This is a special identifier that represents anyone who is authenticated with a Google account or a service account. Users who are not authenticated, such as anonymous visitors, are not included.

#### allUsers <a id="allusers"></a>

This is a special identifier that represents anyone who is on the internet, including authenticated and unauthenticated users. Note that some GCP APIs require authentication of any user accessing the service, and in those cases, allUsers will only imply authorization for all authenticated users.

## Concepts related to access management

When an authenticated member attempts to access a resource, Cloud IAM checks the resource's Cloud IAM policy to determine whether the action is allowed.

### Resource

 You can grant access to users for a GCP resource. Some examples of resources are [projects](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy#projects), [Compute Engine instances](https://cloud.google.com/compute/docs/instances/), and [Cloud Storage buckets](https://cloud.google.com/storage/docs/key-terms).

### Permissions

 Permissions determine what operations are allowed on a resource. In the Cloud IAM world, permissions are represented in the form of `<service>.<resource>.<verb>`, for example `pubsub.subscriptions.consume`.  You don't assign permissions to users directly. Instead, you assign them a **Role** which contains one or more permissions.

### Roles

A role is a collection of permissions. You cannot assign a permission to the user directly; instead you grant them a role. When you grant a role to a user, you grant them all the permissions that the role contains.

### IAM Policy

 You can grant roles to users by creating a _Cloud IAM policy_, which is a collection of statements that define who has what type of access. A policy is attached to a resource and is used to enforce access control whenever that resource is accessed.

![IAM policy](../../.gitbook/assets/image%20%288%29.png)

 A Cloud IAM policy is represented by the IAM `Policy` object. An IAM `Policy` object consists of a list of bindings. A `Binding` binds a list of `members` to a `role`.

`role` is the role you want to assign to the member. The `role` is specified in the form of `roles/<name of the role>`. For example, `roles/storage.objectAdmin`, `roles/storage.objectCreator`, and `roles/storage.objectViewer`.

`members` contains a list of one or more identities as described in the [Concepts related to identity](https://cloud.google.com/iam/docs/overview#concepts_related_identity) section above. 

The Cloud IAM methods are:

* `setIamPolicy()`: Allows you to set policies on your resources.
* `getIamPolicy()`: Allows you to get a policy that was previously set.
* `testIamPermissions()`: Allows you to test whether the caller has the specified permissions for a resource.

The following code snippet shows the structure of a Cloud IAM policy.

```text
{
  "bindings": [
   {
     "role": "roles/storage.objectAdmin",
     "members": [
       "user:alice@example.com",
       "serviceAccount:my-other-app@appspot.gserviceaccount.com",
       "group:admins@example.com",
       "domain:google.com" ]
   },
   {
     "role": "roles/storage.objectViewer",
     "members": ["user:bob@example.com"]
   }
   ]
}
```
