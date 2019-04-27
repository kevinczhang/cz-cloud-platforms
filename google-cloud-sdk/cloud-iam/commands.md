# Commands

## Role

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

## Policy

#### Get policy <a id="get_policy"></a>

```text
gcloud projects get-iam-policy [PROJECT] --format [FORMAT] > [FILE-PATH]
```

\[PROJECT\] is the name of the project. \[FORMAT\] is either JSON or YAML. \[FILE-PATH\] is the path on disk to save the policy.

#### Set policy <a id="set_policy"></a>

Once you have modified the policy to grant the desired roles, call `setIamPolicy()` to make the updates.

Execute the [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/projects/set-iam-policy) command with the path to the JSON file containing the updated policy:

```text
gcloud projects set-iam-policy [PROJECT] [FILE-PATH]
```

As with `get-iam-policy`, \[PROJECT\] is the name of the project to set policy for. \[FILE-PATH\] is the path to the file that contains the new policy.





