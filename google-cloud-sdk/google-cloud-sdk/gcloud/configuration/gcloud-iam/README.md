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

## Grant or revoke role

**To grant a role:**

```text
gcloud [GROUP] add-iam-policy-binding [RESOURCE-NAME]
  --member user:[USER-EMAIL] --role [ROLE-ID]
```

**To revoke a role:**

```text
gcloud [GROUP] remove-iam-policy-binding [RESOURCE-NAME]
  --member user:[EMAIL] --role [ROLE-ID]
```

\[GROUP\] is the `gcloud` group for the resource you want to grant permissions for, such as `projects` or `organizations`. \[RESOURCE\] is the name of the resource. \[EMAIL\] is the user to grant the role to. \[ROLE-ID\] is the ID of the role to grant.

The example below grants the Viewer role to _user-1@gmail.com_ for the project _my-project_ \(note that you can only add Owner role to a project through the console\)

```text
gcloud projects add-iam-policy-binding my-project
  --member user:user-1@gmail.com --role roles/viewer
```

## Cloud IAM policy

#### Get policy <a id="get_policy"></a>

```text
gcloud projects get-iam-policy [PROJECT] --format [FORMAT] > [FILE-PATH]
```

\[PROJECT\] is the name of the project. \[FORMAT\] is either JSON or YAML. \[FILE-PATH\] is the path on disk to save the policy.

For example, the following gets the policy for the project _my-project_ in JSON format and saves it to the user's home directory.

```text
gcloud projects get-iam-policy my-project --format json > ~/policy.json
```

#### Set policy <a id="set_policy"></a>

Execute the [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/projects/set-iam-policy) command with the path to the JSON file containing the updated policy:

```text
gcloud projects set-iam-policy [PROJECT] [FILE-PATH]
```

As with `get-iam-policy`, \[PROJECT\] is the name of the project to set policy for. \[FILE-PATH\] is the path to the file that contains the new policy.

The response will be the updated policy.

