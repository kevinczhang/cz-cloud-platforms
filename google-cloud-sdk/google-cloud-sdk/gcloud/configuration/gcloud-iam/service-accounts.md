# service-accounts

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

To add an IAM policy binding for the role of 'roles/editor' for the user 'test-user@gmail.com' on a service account with identifier 'my-iam-account@somedomain.com', run:

```text
  $ gcloud iam service-accounts add-iam-policy-binding \
      my-iam-account@somedomain.com \
      --member='user:test-user@gmail.com' --role='roles/editor'
```

To add an IAM policy binding for the role of 'roles/editor' to the service account 'test-proj1@example.domain.com', run:

```text
  $ gcloud iam service-accounts add-iam-policy-binding \
      test-proj1@example.domain.com \
      --member='serviceAccount:test-proj1@example.domain.com' \
      --role='roles/editor'
```

To add an IAM policy binding for the role of 'roles/editor' for all authenticated users on a service account with identifier 'my-iam-account@somedomain.com', run:

```text
  $ gcloud iam service-accounts add-iam-policy-binding \
      my-iam-account@somedomain.com --member='allAuthenticatedUsers' \
      --role='roles/editor'
```

To print the IAM policy for a given service account, run:

```text
  $ gcloud iam service-accounts get-iam-policy \
      my-iam-account@somedomain.com
```

To create a new private key for a service account, and save a copy of it locally, run:

```text
  $ gcloud iam service-accounts keys create \
      --iam-account my-iam-account@somedomain.com key.json
```

To list all user-managed keys created before noon on July 19th, 2015 \(to perform key rotation, for example\), run:

```text
  $ gcloud iam service-accounts keys list \
      --iam-account my-iam-account@somedomain.com --managed-by user \
      --created-before 2015-07-19T12:00:00Z
```

## Create an instance with service account

```text
gcloud compute instances create [INSTANCE_NAME] \
    --service-account [SERVICE_ACCOUNT_EMAIL] \
    --scopes [SCOPES,...]
```

where:

* `[SERVICE_ACCOUNT_EMAIL]` is the service account email you want to use. For example: `my-sa-123@my-project-123.iam.gserviceaccount.com`. If you don't know what the email is, learn how to [obtain a service account email](https://cloud.google.com/compute/docs/access/create-enable-service-accounts-for-instances#serviceaccountname).
* `[INSTANCE_NAME]` is the name of the instance.
* `[SCOPES]` is a comma-separated list of full [scope URIs](https://developers.google.com/identity/protocols/googlescopes), or [scope aliases](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create) provided in the description for the `--scopes` flag.

For example:

```text
gcloud compute instances create example-vm \
    --service-account 123-my-sa@my-project-123.iam.gserviceaccount.com \
    --scopes https://www.googleapis.com/auth/cloud-platform
```

## Add a service account to another project:

1. Create the first service account in project A in the Cloud Console. Activate it using `gcloud auth activate-service-account`.
2. In the Cloud Console, navigate to project B. Find the "IAM & admin" &gt; "IAM" page. Click the "Add" button. In the "New members" field paste the name of the service account \(it should look like a strange email address\) and give it the appropriate role.
3. Run `gcloud` commands with `--project` set to project B. They should succeed \(I just manually verified that this will work\).

