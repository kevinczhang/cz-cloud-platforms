---
description: gcloud app - manage your App Engine deployments
---

# gcloud app

```text
gcloud app GROUP | COMMAND [GCLOUD_WIDE_FLAG …]
```

The gcloud app command group lets you deploy and manage your Google App Engine apps. These commands replace their equivalents in the appcfg tool.

App Engine is a platform for building scalable web applications and mobile backends. App Engine provides you with built-in services and APIs such as NoSQL datastores, memcache, and a user authentication API, common to most applications.

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

