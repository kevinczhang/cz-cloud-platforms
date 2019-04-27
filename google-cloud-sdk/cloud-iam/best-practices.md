# Best practices

## Cloud Platform resource hierarchy

IAM allows you to set policies at the following levels of the resource hierarchy:

* **Organization level**. The Organization resource represents your company. IAM roles granted at this level are inherited by all resources under the organization.
* **Project level**. Projects represent a trust boundary within your company. Services within the same project have a default level of trust. IAM roles granted at the project level are inherited by resources within that project.
* **Resource level**. In addition to the existing Cloud Storage and BigQuery ACL systems, additional resources such as Genomics Datasets, Pub/Sub topics, and Compute Engine instances support lower-level roles so that you can grant certain users permission to a single resource within a project.

IAM policies are hierarchical and propagate down the structure. The effective policy for a resource is the union of the policy set at that resource and the policy inherited from its parent.

The owner, editor, and viewer roles are concentric; that is, the owner role includes the permissions in the editor role and the editor role includes the permissions of the viewer role. If you grant both the broader and limited role \(such as editor and the viewer\) to the same person, only the broader role is granted to them.

* Use the security principle of [least privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege) to grant Cloud IAM roles; that is, only give the least amount of access necessary to your resources.
* Grant roles to a Google group instead of to individual users when possible. It is easier to manage members in a Google group than to update a Cloud IAM policy.
* Remember that a policy set on a child resource cannot restrict access granted on its parent. Check the policy granted on every resource and understand the hierarchical inheritance.

## Service account

A service account can have zero or more pairs of service account keys, which are used to authenticate to Google.

One of the features of IAM service accounts is that you can treat it both as a [resource](https://cloud.google.com/iam/docs/overview#resource) and as an [identity](https://cloud.google.com/iam/docs/overview#concepts_related_to_identity).

* When treating the service account as an identity, you can grant a role to a service account, enabling it to access a resource \(such as a project\).
* When treating a service account as a resource, you can grant permission to a user to access that service account. You can grant the Owner, Editor, Viewer, or [Service Account User](https://cloud.google.com/iam/docs/service-accounts#the_service_account_user_role) role to a user to access the service account.

#### Best practices

* Take advantage of the [IAM service account API](https://cloud.google.com/iam/reference/rest/v1/projects.serviceAccounts.keys) to implement key rotation.
* Do not delete service accounts that are in use by running instances on Google App Engine or Google Compute Engine.
* Use the display name of a service account to keep track of the service accounts. When you create a service account, populate its display name with the purpose of the service account.

