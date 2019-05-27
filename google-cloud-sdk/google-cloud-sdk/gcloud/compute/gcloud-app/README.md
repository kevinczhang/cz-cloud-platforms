---
description: gcloud app - manage your App Engine deployments
---

# gcloud app

```text
gcloud app GROUP | COMMAND [GCLOUD_WIDE_FLAG …]
```

`GROUP` is one of the following:

* [`domain-mappings`](https://cloud.google.com/sdk/gcloud/reference/app/domain-mappings)View and manage your App Engine domain mappings.
* [`firewall-rules`](https://cloud.google.com/sdk/gcloud/reference/app/firewall-rules)View and manage your App Engine firewall rules.
* [`instances`](https://cloud.google.com/sdk/gcloud/reference/app/instances)View and manage your App Engine instances.
* [`logs`](https://cloud.google.com/sdk/gcloud/reference/app/logs)Manage your App Engine logs.
* [`operations`](https://cloud.google.com/sdk/gcloud/reference/app/operations)View and manage your App Engine Operations.
* [`regions`](https://cloud.google.com/sdk/gcloud/reference/app/regions)View regional availability of App Engine runtime environments.
* [`services`](https://cloud.google.com/sdk/gcloud/reference/app/services)View and manage your App Engine services.
* [`ssl-certificates`](https://cloud.google.com/sdk/gcloud/reference/app/ssl-certificates)View and manage your App Engine SSL certificates.
* [`versions`](https://cloud.google.com/sdk/gcloud/reference/app/versions)View and manage your App Engine versions.

`COMMAND` is one of the following:

* [`browse`](https://cloud.google.com/sdk/gcloud/reference/app/browse)Open the current app in a web browser.
* [`create`](https://cloud.google.com/sdk/gcloud/reference/app/create)Create an App Engine app within the current Google Cloud Project.
* [`deploy`](https://cloud.google.com/sdk/gcloud/reference/app/deploy)Deploy the local code and/or configuration of your app to App Engine.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/app/describe)Display all data about an existing service.
* [`open-console`](https://cloud.google.com/sdk/gcloud/reference/app/open-console)Open the App Engine dashboard, or log viewer, in a web browser.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/app/update)Updates an App Engine application.

The gcloud app command group lets you deploy and manage your Google App Engine apps. 

## Common commands

To list all versions of all services of your existing deployments, run:

```text
  $ gcloud app versions list
```

To generate all relevant config files for `~/my_app` \(or emit an error message if the directory contents are not recognized\), run:

```text
  $ gcloud app gen-config ~/my_app
```

To open a specific version, run:

```text
  $ gcloud app browse --service="myService" --version="v1"
```

To create an app in the us-central region, run:

```text
  $ gcloud app create --region=us-central
```

 To show all the data about the current application, run

```text
  $ gcloud app describe
```

