---
description: >-
  GCP offers Cloud IAM, which lets you manage access control by defining who
  (identity) has what access (role) for which resource.
---

# Cloud IAM

## Overview

![Cloud IAM](../../.gitbook/assets/image%20%2822%29.png)

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

## Basic Concepts

When an authenticated member attempts to access a resource, Cloud IAM checks the resource's Cloud IAM policy to determine whether the action is allowed.

### Resource

You can grant access to users for a GCP resource. Some examples of resources are [projects](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy#projects), [Compute Engine instances](https://cloud.google.com/compute/docs/instances/), and [Cloud Storage buckets](https://cloud.google.com/storage/docs/key-terms).

### Permissions

Permissions determine what operations are allowed on a resource. In the Cloud IAM world, permissions are represented in the form of `<service>.<resource>.<verb>`, for example `pubsub.subscriptions.consume`.  You don't assign permissions to users directly. Instead, you assign them a **Role** which contains one or more permissions.

### Roles

A role is a collection of permissions. You cannot assign a permission to the user directly; instead you grant them a role. When you grant a role to a user, you grant them all the permissions that the role contains.

### IAM Policy

 You can grant roles to users by creating a _Cloud IAM policy_, which is a collection of statements that define who has what type of access. A policy is attached to a resource and is used to enforce access control whenever that resource is accessed.

## Cloud Platform resource hierarchy

IAM allows you to set policies at the following levels of the resource hierarchy:

* **Organization level**. The Organization resource represents your company. IAM roles granted at this level are inherited by all resources under the organization.
* **Project level**. Projects represent a trust boundary within your company. Services within the same project have a default level of trust. IAM roles granted at the project level are inherited by resources within that project.
* **Resource level**. In addition to the existing Cloud Storage and BigQuery ACL systems, additional resources such as Genomics Datasets, Pub/Sub topics, and Compute Engine instances support lower-level roles so that you can grant certain users permission to a single resource within a project.

**IAM policies are hierarchical and propagate down the structure. The effective policy for a resource is the union of the policy set at that resource and the policy inherited from its parent.**

The owner, editor, and viewer roles are concentric; that is, the owner role includes the permissions in the editor role and the editor role includes the permissions of the viewer role. If you grant both the broader and limited role \(such as editor and the viewer\) to the same person, only the broader role is granted to them.

* Use the security principle of [least privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege) to grant Cloud IAM roles; that is, only give the least amount of access necessary to your resources.
* Grant roles to a Google group instead of to individual users when possible. It is easier to manage members in a Google group than to update a Cloud IAM policy.
* **Remember that a policy set on a child resource cannot restrict access granted on its parent.** Check the policy granted on every resource and understand the hierarchical inheritance.

## Audit Logging

It consists of two log streams for each project: Admin Activity and Data Access, which are generated by GCP services to help you answer the question of "who did what, where, and when?" within your GCP projects. These logs are distinct from your application logs, and are described below:

* [Admin Activity logs](https://cloud.google.com/logging/docs/audit#admin-activity) contain log entries for API calls or other administrative actions that modify the configuration or metadata of resources. Admin Activity logs are always enabled. There is no charge for your Admin Activity audit logs.
* [Data Access logs](https://cloud.google.com/logging/docs/audit#data-access) record API calls that create, modify, or read user-provided data. Data Access audit logs are disabled by default because they can be large.

 It is important to note that log entries are held in Stackdriver for a limited time known as the [retention period](https://cloud.google.com/logging/quotas#logs_retention_periods). After that, the entries are deleted. To keep log entries longer they must be [exported](https://cloud.google.com/logging/docs/export) outside of Stackdriver to Cloud Pub/Sub, BigQuery, or a Cloud Storage bucket.

