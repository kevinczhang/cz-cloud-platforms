---
description: >-
  Google Cloud SDK is a set of tools that you can use to manage resources and
  applications hosted on Google Cloud Platform. These include the gcloud,
  gsutil, and bq command line tools.
---

# Google Cloud SDK

The Cloud SDK is a set of tools for Cloud Platform. It contains gcloud, gsutil, and bq command-line tools, which you can use to access Google Compute Engine, Google Cloud Storage, Google BigQuery, and other products and services from the command-line. You can run these tools interactively or in your automated scripts.

### Run Local Service Emulators <a id="run-local-service-emulators"></a>

Cloud SDK emulators for Google Cloud Pub/Sub and Google Cloud Datastore allow you to simulate these services in your environment for local development, testing and validation. You start and manage service emulators using the gcloud command-line tool.

## Managing Cloud SDK Components

#### Listing components <a id="listing_components"></a>

To see a list of components that are available and currently installed, run [`gcloud components list`](https://cloud.google.com/sdk/gcloud/reference/components/list):

```text
gcloud components list
```

#### Installing components <a id="installing_components"></a>

To install a component at the current version of your Cloud SDK installation, run [`gcloud components install`](https://cloud.google.com/sdk/gcloud/reference/components/install):

```text
gcloud components install [COMPONENT-ID]
```

#### Updating components <a id="updating_components"></a>

Use the [`gcloud components update`](https://cloud.google.com/sdk/gcloud/reference/components/update) command to update all installed components to the latest available version of Cloud SDK:

```text
gcloud components update
```

#### Removing components <a id="removing_components"></a>

Use the [`gcloud components remove`](https://cloud.google.com/sdk/gcloud/reference/components/remove) command to remove a specified component by its ID:

```text
gcloud components remove [COMPONENT-ID]
```

