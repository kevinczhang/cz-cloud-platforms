---
description: >-
  The gcloud iam command group lets you manage Google Cloud Identity & Access
  Management (IAM) service accounts and keys.
---

# gcloud iam

`gcloud iam` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/iam/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/iam/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/iam/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:

* [`roles`](https://cloud.google.com/sdk/gcloud/reference/iam/roles)Create and manipulate roles.
* [`service-accounts`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts)Create and manipulate service accounts.

`COMMAND` is one of the following:

* [`list-grantable-roles`](https://cloud.google.com/sdk/gcloud/reference/iam/list-grantable-roles)List IAM grantable roles for a resource.
* [`list-testable-permissions`](https://cloud.google.com/sdk/gcloud/reference/iam/list-testable-permissions)List IAM testable permissions for a resource.

## gcloud iam list-grantable-roles

This command displays the list of grantable roles for a resource. The resource can be referenced either via the full resource name or via a URI.

`gcloud iam list-grantable-roles` [`RESOURCE`](https://cloud.google.com/sdk/gcloud/reference/iam/list-grantable-roles#RESOURCE) \[[`--filter`](https://cloud.google.com/sdk/gcloud/reference/iam/list-grantable-roles#--filter)=`EXPRESSION`\]\[[`--page-size`](https://cloud.google.com/sdk/gcloud/reference/iam/list-grantable-roles#--page-size)=`PAGE_SIZE`; default=100\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/iam/list-grantable-roles#GCLOUD-WIDE-FLAGS) `…`\]

To get a URI from most `list` commands in [`gcloud`](https://cloud.google.com/sdk/gcloud/reference), pass the `--uri`flag. For example:

```text
  $ gcloud compute instances list --project prj --uri
  https://www.googleapis.com/compute/v1/projects/prj/zones/us-east1-c/instances/i1
  https://www.googleapis.com/compute/v1/projects/prj/zones/us-east1-d/instances/i2
```

List grantable roles for a project:

```text
  $ gcloud iam list-grantable-roles \
      //cloudresourcemanager.googleapis.com/projects/PROJECT_ID
```

List grantable roles for a resource identified via full resource name:

```text
  $ gcloud iam list-grantable-roles \
      //compute.googleapis.com/projects/example-project/zones/\
  us-central1-f/instances/example-instance
```

List grantable roles for a resource identified via URI:

```text
  $ gcloud iam list-grantable-roles \
      https://www.googleapis.com/compute/v1/projects/example-project/\
  zones/us-central1-f/instances/example-instance
```

## gcloud iam roles

Create and manipulate roles.

`gcloud iam roles` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`copy`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/copy)Create a role from an existing role.
* [`create`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/create)Create a custom role for a project or an organization.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/delete)Delete a custom role from an organization or a project.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/describe)Show metadata for a role.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/list)List the roles defined at a parent organization or a project.
* [`undelete`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/undelete)Undelete a custom role from an organization or a project.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/update)Update an IAM custom role.

To list the roles for a project, run:

```text
  $ gcloud iam roles list --project myproject
```

To create a custom role with flags, run:

```text
  $ gcloud iam roles create editor --project myproject \
      --title myrole --description \
      "Have access to get and update the project" --permissions \
      resourcemanager.projects.get,resourcemanager.projects.update
```

## gcloud iam service-accounts

Create and manipulate IAM service accounts.

`gcloud iam service-accounts` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:[`keys`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/keys)Manage service account keys.

`COMMAND` is one of the following:

* [`add-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/add-iam-policy-binding)Add an IAM policy binding to an IAM Service Account.
* [`create`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/create)Create a service account for a project.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/delete)Delete a service account from a project.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/describe)Show metadata for a service account from a project.
* [`get-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/get-iam-policy)Get the IAM policy for a service account.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/list)List all of a project's service accounts.
* [`remove-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/remove-iam-policy-binding)Remove IAM policy binding of a service account.
* [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/set-iam-policy)Set IAM policy for a service account.
* [`sign-blob`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/sign-blob)Sign a blob with a managed service account key.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/update)Update an IAM service account.

`gcloud iam service-accounts create` [`NAME`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/create#NAME) \[[`--display-name`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/create#--display-name)=`DISPLAY_NAME`\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/create#GCLOUD-WIDE-FLAGS) `…`\]

To create a service account for your project, run:

```text
  $ gcloud iam service-accounts create some-account-name \
      --display-name "My Service Account"
```



