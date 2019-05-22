---
description: >-
  Google Cloud Functions, GCP's functions as a service (FaaS) offering, provides
  a serverless execution environment for building and connecting cloud services.
---

# Cloud Functions

### Cloud Functions are a good choice for use cases that include:

* Data processing and ETL operations, for scenarios such as video transcoding and IoT streaming data.
* Webhooks to respond to HTTP triggers.
* Lightweight APIs that comprise loosely coupled logic into applications.
* Mobile backend functions.
* You code executes within the limits.

Cloud Functions can be written using JavaScript, Python 3, or Go runtimes on Google Cloud Platform. Cloud Functions removes the work of managing servers, configuring software, updating frameworks, and patching operating systems.

Cloud Functions have access to the Google Service Account credential and are thus seamlessly authenticated with the majority of Google Cloud Platform services.

## Events

Your function is triggered when an event being watched is fired. Cloud events are _things_ that happen in your cloud environment. Currently, Cloud Functions supports events from the following providers:

* [HTTP](https://cloud.google.com/functions/docs/calling/http)—invoke functions directly via HTTP requests.
* [Cloud Storage](https://cloud.google.com/storage/)
* [Cloud Pub/Sub](https://cloud.google.com/pubsub/)
* [Cloud Firestore](https://cloud.google.com/firestore/)
* [Firebase \(Realtime Database, Storage, Analytics, Auth\)](https://firebase.google.com/)
* [Stackdriver Logging](https://cloud.google.com/logging/)—forward log entries to a Pub/Sub topic by [creating a sink](https://cloud.google.com/logging/docs/export/configure_export_v2#dest-create). You can then [trigger the function](https://cloud.google.com/functions/docs/calling/pubsub).

## Use cases

| Use case | Description |
| :--- | :--- |
| Data processing / ETL | Listen and respond to [Cloud Storage](https://cloud.google.com/storage/) events such as when a file is created, changed, or removed. Process images, perform video transcoding, validate and transform data, and invoke any service on the internet from your Cloud Functions. |
| Webhooks | Via a simple [HTTP trigger](https://cloud.google.com/functions/docs/calling/http), respond to events originating from 3rd party systems like GitHub, Slack, Stripe, or from anywhere that can send HTTP requests. |
| Lightweight APIs | Compose applications from lightweight, loosely coupled bits of logic that are quick to build and that scale instantly. Your functions can be event-driven or invoked directly over HTTP/S. |
| Mobile backend | Use Google’s mobile platform for app developers, [Firebase](https://firebase.google.com/docs/functions/), and write your mobile backend in Cloud Functions. Listen and respond to events from Firebase Analytics, Realtime Database, Authentication, and Storage. |
| IoT | Imagine tens or hundreds of thousands of devices streaming data into Cloud Pub/Sub, thereby launching Cloud Functions to process, transform and store data. Cloud Functions lets you do it in a way that’s completely serverless. |

