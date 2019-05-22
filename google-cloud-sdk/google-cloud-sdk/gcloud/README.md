---
description: >-
  The gcloud command-line interface is a tool that provides the primary CLI to
  Google Cloud Platform.
---

# gcloud

## Command format

_**gcloud - manage Google Cloud Platform resources and developer workflow**_

[`gcloud`](https://cloud.google.com/sdk/gcloud/reference/#gcloud) [**`GROUP`**](https://cloud.google.com/sdk/gcloud/reference/#GROUP) \| [**`COMMAND`**](https://cloud.google.com/sdk/gcloud/reference/#COMMAND) \[[`--account`](https://cloud.google.com/sdk/gcloud/reference/#--account)=**`ACCOUNT`**\] \[[`--configuration`](https://cloud.google.com/sdk/gcloud/reference/#--configuration)=**`CONFIGURATION`**\]\[[`--flags-file`](https://cloud.google.com/sdk/gcloud/reference/#--flags-file)=**`YAML_FILE`**\] \[[`--flatten`](https://cloud.google.com/sdk/gcloud/reference/#--flatten)=\[**`KEY`**,…\]\] \[[`--format`](https://cloud.google.com/sdk/gcloud/reference/#--format)=**`FORMAT`**\] \[[`--help`](https://cloud.google.com/sdk/gcloud/reference/#--help)\]\[[`--project`](https://cloud.google.com/sdk/gcloud/reference/#--project)=**`PROJECT_ID`**\] \[[`--quiet`](https://cloud.google.com/sdk/gcloud/reference/#--quiet), [`-q`](https://cloud.google.com/sdk/gcloud/reference/#-q)\] \[[`--verbosity`](https://cloud.google.com/sdk/gcloud/reference/#--verbosity)=**`VERBOSITY`**; default="warning"\] \[[`--version`](https://cloud.google.com/sdk/gcloud/reference/#--version), [`-v`](https://cloud.google.com/sdk/gcloud/reference/#-v)\]\[[`-h`](https://cloud.google.com/sdk/gcloud/reference/#-h)\] \[[`--impersonate-service-account`](https://cloud.google.com/sdk/gcloud/reference/#--impersonate-service-account)=**`SERVICE_ACCOUNT_EMAIL`**\] \[[`--log-http`](https://cloud.google.com/sdk/gcloud/reference/#--log-http)\]\[[`--trace-token`](https://cloud.google.com/sdk/gcloud/reference/#--trace-token)=**`TRACE_TOKEN`**\] \[[`--no-user-output-enabled`](https://cloud.google.com/sdk/gcloud/reference/#--user-output-enabled)\]

**GROUP :** group is Google Cloud platform service name or type of command

e.g.  compute \(virtual machine \), pubsub, spanner etc as service

         alpha, beta etc as type of command   

_This gets more complex when you have hierarchy of resources like_

```text
gcloud compute instance list
```

-&gt; compute is service, and "instance list" asking list of instance of VM. 

-&gt; All of this considered inside groups i.e. service operations.

_**For Exam sequence is important.  like compute should always comes 1st and than instance.**_

**COMMAND :** Action on service or generic action.

e.g. info, help, 

**Optional gcloud params -&gt;**   **Very Important for exam.**

gcloud either use env variable/project settings if you set so e.g. Default Project, Default Region, Default Zone. 

## Initializing Cloud SDK

`gcloud init` performs the following setup steps:

* [Authorizes](https://cloud.google.com/sdk/docs/authorizing) Cloud SDK tools to use your user account credentials to access Google Cloud Platform, or lets you select an account if you have previously authorized access
* Sets up a Cloud SDK [configuration](https://cloud.google.com/sdk/docs/configurations) and sets a base set of [properties](https://cloud.google.com/sdk/docs/properties), including the active account from the step above, the current project, and if applicable, the default Google Compute Engine region and zone

You can run the following as alternatives to `gcloud init`:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Command</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="https://cloud.google.com/sdk/gcloud/reference/auth/login"><code>gcloud auth login</code></a>
      </td>
      <td style="text-align:left">Authorize with a user account without setting up a configuration.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://cloud.google.com/sdk/gcloud/reference/auth/activate-service-account"><code>gcloud auth activate-service-account</code></a>
      </td>
      <td style="text-align:left">
        <p>Authorize with a service account instead of a user account.</p>
        <p>Useful for authorizing non-interactively and without a web browser.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://cloud.google.com/sdk/gcloud/reference/config"><code>gcloud config [COMMAND]</code> <br /></a>
        <a
        href="https://cloud.google.com/sdk/gcloud/reference/config/configurations"><code>gcloud config configurations [COMMAND]</code>
          </a>
      </td>
      <td style="text-align:left">Create and manage Cloud SDK configurations and properties.</td>
    </tr>
  </tbody>
</table>## Authorizing SDK Tools

### Connect

```text
gcloud auth application-default login
```

### Listing accounts <a id="listing_accounts"></a>

```text
gcloud auth list
```

### Switching the active account <a id="switching_the_active_account"></a>

To switch the active account, run [`gcloud config set`](https://cloud.google.com/sdk/gcloud/reference/config/set):

```text
gcloud config set account [ACCOUNT]
```

where `[ACCOUNT]` is the full e-mail address of the account.

You can also switch accounts by creating a separate configuration that specifies the different account and switching between configurations:

```text
gcloud config configurations activate [CONFIGURATION]
```

If you want to switch the account used by the gcloud CLI on a per-invocation basis, override the active account using the [`--account`](https://cloud.google.com/sdk/gcloud/reference/) flag.

### Finding your credential files <a id="finding_your_credential_files"></a>

To find the location of your credential files, run [`gcloud info`](https://cloud.google.com/sdk/gcloud/reference/info):

```text
gcloud info
```

### Revoking credentials for an account <a id="revoking_credentials_for_an_account"></a>

To revoke credentials, run: [`gcloud auth revoke`](https://cloud.google.com/sdk/gcloud/reference/auth/revoke):

```text
gcloud auth revoke [ACCOUNT]
```

## Others

### Disabling prompts <a id="disabling_prompts"></a>

You can disable prompts from gcloud CLI commands by setting the [`disable_prompts`](https://cloud.google.com/sdk/gcloud/guide/properties) property in your [configuration](https://cloud.google.com/sdk/gcloud/guide/configurations) to `True` or by using the global [`--quiet`](https://cloud.google.com/sdk/gcloud/reference) or `-q` flag. 

For example:

```text
    gcloud --quiet debug targets list
```

### Handling output <a id="handling_output"></a>

* **Don't depend on messages printed to standard error.**
* **Don't depend on the raw output of messages printed to standard output.** You can modify the default output from [`--format`](https://cloud.google.com/sdk/gcloud/reference/topic/formats) by using [`projections`](https://cloud.google.com/sdk/gcloud/reference/topic/projections). For increased granularity, use the [`--filter` flag](https://cloud.google.com/sdk/gcloud/reference/topic/filters) to return a subset of the values based on an expression. You can then script against those returned values.
* **Do depend on command exit status.**

**Example script**

```text
    gcloud projects list \
    --format="table(projectNumber,projectId,createTime)" \
    --filter="createTime.date('%Y-%m-%d', Z)='2016-05-11'"
```

\*\*\*\*

