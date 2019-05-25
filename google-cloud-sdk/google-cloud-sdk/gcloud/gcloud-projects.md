---
description: >-
  The gcloud projects group lets you create and manage IAM policies for projects
  on the Google Cloud Platform.
---

# gcloud projects

Resources are organized hierarchically and assigned to a particular project. A Project resource is required to use Google Cloud Platform, and forms the basis for creating, enabling and using all Cloud Platform services, managing APIs, enabling billing, adding and removing collaborators, and managing permissions.

`gcloud projects` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/projects/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/projects/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`add-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/projects/add-iam-policy-binding)Add IAM policy binding for a project.
* [`create`](https://cloud.google.com/sdk/gcloud/reference/projects/create)Create a new project.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/projects/delete)Delete a project.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/projects/describe)Show metadata for a project.
* [`get-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/projects/get-iam-policy)Get IAM policy for a project.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/projects/list)List projects accessible by the active account.
* [`remove-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/projects/remove-iam-policy-binding)Remove IAM policy binding for a project.
* [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/projects/set-iam-policy)Set IAM policy for a project.
* [`undelete`](https://cloud.google.com/sdk/gcloud/reference/projects/undelete)Undelete a project.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/projects/update)Update the name of a project.

## projects create

 The following command creates a project with ID `example-foo-bar-1`, name `Happy project` and label `type=happy`:

```text
  $ gcloud projects create example-foo-bar-1 --name="Happy project" \
      --labels=type=happy
```

By default, projects are not created under a parent resource. The following command creates a project with ID `example-2` with parent `folders/12345`:

```text
  $ gcloud projects create example-2 --folder=12345
```

The following command creates a project with ID `example-3` with parent `organizations/2048`:

```text
  $ gcloud projects create example-3 --organization=2048
```

## iam-policy

 To add an IAM policy binding for the role of 'roles/editor' for the user 'test-user@gmail.com' on a project with identifier 'example-project-id-1', run:

```text
  $ gcloud projects add-iam-policy-binding example-project-id-1 \
      --member='user:test-user@gmail.com' --role='roles/editor'
```

To add an IAM policy binding for the role of 'roles/editor' to the service account 'test-proj1@example.domain.com', run:

```text
  $ gcloud projects add-iam-policy-binding \
      test-proj1@example.domain.com \
      --member='serviceAccount:test-proj1@example.domain.com' \
      --role='roles/editor'
```

To add an IAM policy binding for the role of 'roles/editor' for all authenticated users on a project with identifier 'example-project-id-1', run:

```text
  $ gcloud projects add-iam-policy-binding example-project-id-1 \
      --member='allAuthenticatedUsers' --role='roles/editor'
```

 The following command reads an IAM policy defined in a JSON file `policy.json` and sets it for a project with the ID `example-project-id-1`:

```text
  $ gcloud projects set-iam-policy example-project-id-1 policy.json
```

