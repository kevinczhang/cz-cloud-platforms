---
description: An App Engine application can consume resources up to certain quotas.
---

# Quotas

App Engine has three kinds of quotas or limits:

* **Free quotas:** Every application gets an amount of each resource for free. Free quotas can only be exceeded by paid applications, up to the application's spending limit or the safety limit, whichever applies first.
* **Spending limits:** If you are the [project owner](https://cloud.google.com/appengine/docs/standard/python/access-control#owner) and the [billing administrator](https://support.google.com/cloud/answer/6293536), you can set the spending limit to manage application costs in the Google Cloud Platform Console in the [App Engine Settings](https://console.cloud.google.com/appengine/settings). Spending limits might be exceeded slightly as the application is disabled.
* **Safety limits:** Safety limits are set by Google to protect the integrity of the App Engine system. These quotas ensure that no single app can over-consume resources to the detriment of other apps. If you go above these limits you'll get an error whether you are paid or free.

Safety limits include _daily quotas_ and _per-minute quotas_:

* **Daily quotas** are refreshed daily at midnight Pacific time. Paid applications can exceed this free quota until their spending limit is exhausted, or until the safety limit is reached, whichever comes first.
* **Per-minute quotas** protect the application from consuming all of its resources in very short periods of time, and prevent other applications from monopolizing a given resource. If your application consumes a resource too quickly and depletes one of the per-minute quotas, the word "Limited" appears next to the appropriate quota on the **Quota Details** screen in the GCP Console. Requests for resources that have hit their per-minute maximum will be denied.

