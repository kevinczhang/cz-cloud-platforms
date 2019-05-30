# gcloud spanner instances

## Manage Cloud Spanner instances

`gcloud spanner instances` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/#GCLOUD-WIDE-FLAGS) `…`\]

`COMMAND` is one of the following:

* [`add-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/add-iam-policy-binding)Add IAM policy binding to a Cloud Spanner instance.
* [`create`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/create)Create a Cloud Spanner instance.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/delete)Delete a Cloud Spanner instance.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/describe)Describe a Cloud Spanner instance.
* [`get-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/get-iam-policy)Get the IAM policy for a Cloud Spanner instance.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/list)List the Cloud Spanner instances in this project.
* [`remove-iam-policy-binding`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/remove-iam-policy-binding)Remove IAM policy binding of a Cloud Spanner instance.
* [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/set-iam-policy)Set the IAM policy for a Cloud Spanner instance.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/update)Update a Cloud Spanner instance.

### Create a spanner instance

Use the `gcloud spanner instances create` command:

```text
gcloud spanner instances create [INSTANCE-ID] --config=[INSTANCE-CONFIG] \
    --description="[INSTANCE-NAME]" --nodes=[NODE-COUNT]
```

Provide the following values:

* `[INSTANCE-ID]`: A permanent identifier that is unique within your Google Cloud Platform project. You cannot change the instance ID later.
* `[INSTANCE-CONFIG]`: The instance configuration, which defines the geographic location of the instance's nodes and affects how data is replicated. [Learn more about instance configurations](https://cloud.google.com/spanner/docs/instances).
* `[INSTANCE-NAME]`: The name to display for the instance in the GCP Console. The instance name must be unique within your Google Cloud Platform project.
* `[NODE-COUNT]`: The number of nodes for the instance. The number of nodes determines the amount of serving and storage resources that are available to databases in the instance.

For example:

```text
gcloud spanner instances create test-instance --config=regional-us-central1 \
    --description="Test Instance" --nodes=1
```

### Listing instances <a id="list-instances"></a>

Use the `gcloud spanner instances list` command:

```text
gcloud spanner instances list
```

The `gcloud` tool prints a list of your Cloud Spanner instances, along with each instance's ID, display name, configuration, and number of nodes.

### Editing an instance <a id="edit-instance"></a>

Use the `gcloud spanner instances update` command:

```text
gcloud spanner instances update [INSTANCE-ID] --description=[INSTANCE-NAME]
```

Provide the following values:

* `[INSTANCE-ID]`: The permanent identifier for the instance.
* `[INSTANCE-NAME]`: The name to display for the instance in the GCP Console. The instance name must be unique within your Google Cloud Platform project.

### Changing the number of nodes

Use the `gcloud spanner instances update` command:

```text
gcloud spanner instances update [INSTANCE-ID] --nodes=[NODE-COUNT]
```

Provide the following values:

* `[INSTANCE-ID]`: The permanent identifier for the instance.
* `[NODE-COUNT]`: The number of nodes for the instance.

### Deleting an instance <a id="delete-instance"></a>

Use the `gcloud spanner instances delete` command, replacing `[INSTANCE-ID]` with the instance ID:

```text
gcloud spanner instances delete [INSTANCE-ID]
```



