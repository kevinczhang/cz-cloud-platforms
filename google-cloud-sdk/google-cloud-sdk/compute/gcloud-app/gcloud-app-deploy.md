---
description: >-
  gcloud app deploy - deploy the local code and/or configuration of your app to
  App Engine
---

# gcloud app deploy

 `gcloud app deploy` \[[`DEPLOYABLES`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#DEPLOYABLES) …\] \[[`--bucket`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#--bucket)=`BUCKET`\] \[[`--image-url`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#--image-url)=`IMAGE_URL`\] \[[`--no-promote`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#--promote)\]\[[`--no-stop-previous-version`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#--stop-previous-version)\] \[[`--version`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#--version)=`VERSION`, [`-v`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#-v) [`VERSION`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#VERSION)\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/app/deploy#GCLOUD-WIDE-FLAGS) `…`\]

This command is used to deploy both code and configuration to the App Engine server. As an input it takes one or more `DEPLOYABLES` that should be uploaded. A `DEPLOYABLE` can be a service's .yaml file or a configuration's .yaml file.

The yaml files for the services or configurations you want to deploy. If not given, defaults to `app.yaml` in the current directory. If that is not found, attempts to automatically generate necessary configuration files \(such as app.yaml\) in the current directory.

> Note, for Java Standard apps, you must add the path to the `appengine-web.xml` file inside the WEB-INF directory. gcloud app deploy skips files specified in the .gcloudignore file.

## Setting Autoscaling Parameters

If you use the Cloud SDK tooling to deploy your app, such as `gcloud app deploy`, you can set the following autoscaling parameters in the `app.yaml` configuration file:

* `min_instances`
* `max_instances`
* `target_throughput_utilization`
* `target_cpu_utilization`

## Examples

 To deploy a single service, run:

```text
  $ gcloud app deploy ~/my_app/app.yaml
```

To deploy an App Engine Standard Java service, run:

```text
  $ gcloud app deploy ~/my_app/WEB-INF/appengine-web.xml
```

By default, the service is deployed the current project configured via:

```text
  $ gcloud config set core/project PROJECT
```

To override this value for a single deployment, use the `--project` flag:

```text
  $ gcloud app deploy ~/my_app/app.yaml --project=PROJECT
```

To deploy multiple services, run:

```text
  $ gcloud app deploy ~/my_app/app.yaml ~/my_app/another_service.yaml
```

To change the default --promote behavior for your current environment, run:

```text
  $ gcloud config set app/promote_by_default false
```

