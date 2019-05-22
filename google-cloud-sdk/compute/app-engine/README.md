---
description: >-
  Google App Engine is GCP's platform as a service (PaaS). With App Engine,
  Google handles most of the management of the resources for you.
---

# App Engine

Web based workloads, no ops, high-availability.

* You value development over ops
* You want high availability without the 3 A.M. pager calls
* Application portability isn't a primary concern
* **Your application speaks HTTP**
* You don't care about the underlying OS

Upsides:

* Inexpensive
* Fast startup

Downsides:

* No custom runtimes
* No 3rd party binaries
* No writing to disk
* No SSH

The following diagram illustrates the hierarchy of an App Engine app running with multiple services. In this diagram, the app has two services that contain multiple versions, and two of those versions are actively running on multiple instances:

![](../../../.gitbook/assets/image%20%283%29.png)

When you build your app on App Engine, you can:

* Build your app on top of the App Engine [standard environment](https://cloud.google.com/appengine/docs/about-the-standard-environment) runtimes in the languages that the standard environment supports, including: [Python 2.7](https://cloud.google.com/appengine/docs/python/), [Java 8, Java 7](https://cloud.google.com/appengine/docs/java/), [PHP 5.5](https://cloud.google.com/appengine/docs/php/), and [Go 1.8, 1.6](https://cloud.google.com/appengine/docs/go/).
* Build your app on top of the App Engine [flexible environment](https://cloud.google.com/appengine/docs/flexible/) runtimes in the languages that App Engine flexible supports, including: [Python 2.7/3.6](https://cloud.google.com/appengine/docs/flexible/python/), [Java 8](https://cloud.google.com/appengine/docs/flexible/java/), [Go 1.8](https://cloud.google.com/appengine/docs/flexible/go/), [Node.js](https://cloud.google.com/appengine/docs/flexible/nodejs/), [PHP 5.6, 7](https://cloud.google.com/appengine/docs/flexible/php/), [.NET](https://cloud.google.com/appengine/docs/flexible/dotnet/), and [Ruby](https://cloud.google.com/appengine/docs/flexible/ruby/). Or use [custom runtimes](https://cloud.google.com/appengine/docs/flexible/custom-runtimes/) to use an alternative implementation of a supported language or any other language.
* Let Google manage app hosting, scaling, monitoring, and infrastructure for you.
* Use the [App Engine SDK](https://cloud.google.com/appengine/downloads) to develop and test on your local machine in an environment that simulates App Engine on GCP.
* Easily use the [storage technologies](https://cloud.google.com/appengine/features/#storage) that App Engine is designed to support in the standard and flexible environments.

  [Google Cloud SQL](https://cloud.google.com/appengine/features/#cloudsql) is a SQL database, supporting either MySQL or PostgreSQL. [Google Cloud Datastore](https://cloud.google.com/appengine/docs/standard/python/ndb/) is a schemaless, NoSQL datastore. [Google Cloud Storage](https://cloud.google.com/appengine/features/#gcslibrary) provides space for your large files.

  In the standard environment, you can also choose from a variety of third-party databases to use with your applications such as Redis, MongoDB, Cassandra, and Hadoop.

  In the flexible environment, you can easily use any third-party database supported by your language, if the database is accessible from the Google App Engine instance.

  In either environment, these third-party databases can be hosted on Compute Engine, hosted on another cloud provider, hosted on-premises, or managed by a third- party vendor.

* Use [Cloud Endpoints](https://cloud.google.com/appengine/features/#Endpoints) in the standard environment to generate APIs and client libraries that you can use to simplify data access from other applications. Endpoints makes it easier to create a web backend for web clients and mobile clients, such as Android or iOS.
* Use built-in, managed services for activities such as email and user management.
* Use [Cloud Security Scanner](https://cloud.google.com/security-scanner/) to identify security vulnerabilities as a complement to your existing secure design and development processes.
* Deploy your app by using the App Engine launcher GUI application on macOS or Microsoft Windows or by using the command line.
* For the standard environment, run your app from the Central US or Western Europe regions.

For a complete list and description of App Engine's features, see the [App Engine documentation](https://cloud.google.com/appengine/docs/).

