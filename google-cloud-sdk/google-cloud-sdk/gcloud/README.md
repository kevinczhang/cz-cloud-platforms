---
description: >-
  The gcloud command-line interface is a tool that provides the primary CLI to
  Google Cloud Platform.
---

# gcloud

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

