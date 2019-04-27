---
description: >-
  The gcloud command-line interface is a tool that provides the primary CLI to
  Google Cloud Platform.
---

# gcloud

 The gcloud CLI is a part of the [Google Cloud SDK](https://cloud.google.com/sdk/docs/). You must [download and install the SDK](https://cloud.google.com/sdk/downloads) on your system and [initialize it](https://cloud.google.com/sdk/docs/initializing)before you can use the gcloud command-line tool.

### Configurations <a id="configurations"></a>

A configuration is a named set of gcloud CLI properties. It works like a _profile_, essentially.

Starting off with Cloud SDK, you'll work with a single configuration named `default` and you can set properties by running either `gcloud init` or `gcloud config set`. This single default configuration is suitable for most use cases.

If you'd like to work with multiple projects or authorization accounts, you can set up multiple configurations with `gcloud config configurations create` and switch among them accordingly.

