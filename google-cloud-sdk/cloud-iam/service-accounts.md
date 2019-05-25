---
description: >-
  A service account is a special Google account that belongs to your application
  or a virtual machine (VM), instead of to an individual end user.
---

# Service accounts

Your application uses the service account to [call the Google API of a service](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#authorizingrequests), so that the users aren't directly involved. A service account is identified by its email address, which is unique to the account.

#### Service account keys <a id="service_account_keys"></a>

Each service account is associated with a key pair, which is managed by Google Cloud Platform \(GCP\). It is used for service-to-service authentication within GCP. These keys are rotated automatically by Google, and are used for signing for a maximum of two weeks. You can create up to 10 service account keys per service account to facilitate key rotation.

One of the features of IAM service accounts is that you can treat it both as a [resource](https://cloud.google.com/iam/docs/overview#resource) and as an [identity](https://cloud.google.com/iam/docs/overview#concepts_related_to_identity).

* When treating the service account as an identity, you can grant a role to a service account, enabling it to access a resource \(such as a project\).
* When treating a service account as a resource, you can grant permission to a user to access that service account. You can grant the Owner, Editor, Viewer, or [Service Account User](https://cloud.google.com/iam/docs/service-accounts#the_service_account_user_role) role to a user to access the service account.

### Types of service accounts <a id="types_of_service_accounts"></a>

#### 1. User-managed service accounts <a id="user-managed_service_accounts"></a>

Default Compute Engine Service account:

`PROJECT_NUMBER-compute@developer.gserviceaccount.com`

Default App Engine service account:

`PROJECT_ID@appspot.gserviceaccount.com`

User created service account format:

`SERVICE_ACCOUNT_NAME@PROJECT_ID.iam.gserviceaccount.com`

#### 2. Google-managed service accounts <a id="google-managed_service_accounts"></a>

**Google APIs service account**

An example of a Google-managed service account is a Google API service account identifiable using the email:

`PROJECT_NUMBER@cloudservices.gserviceaccount.com`

### Service account permissions <a id="service_account_permissions"></a>

In addition to being an [identity](https://cloud.google.com/iam/docs/overview#concepts_related_to_identity), a service account is a [resource](https://cloud.google.com/iam/docs/overview#resource) which has IAM policies attached to it. These policies determine who can use the service account.

