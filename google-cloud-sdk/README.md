---
description: >-
  Google Cloud SDK is a set of tools that you can use to manage resources and
  applications hosted on Google Cloud Platform. These include the gcloud,
  gsutil, and bq command line tools.
---

# Google Cloud Platform

## Overview

GCP consists of a set of physical assets, such as computers and hard disk drives, and virtual resources, such as virtual machines \(VMs\), that are contained in [Google's data centers](https://www.google.com/about/datacenters/) around the globe. Each data center location is in a global _region_. Regions include Central US, Western Europe, and East Asia. Each region is a collection of _zones_, which are isolated from each other within the region. Each zone is identified by a name that combines a letter identifier with the name of the region.

In cloud computing, what you might be used to thinking of as software and hardware products, become _services_. These services provide access to the underlying resources.

_global resources_ include preconfigured disk images, disk snapshots, and networks. 

_regional resources_ include static external IP addresses. 

_zonal resources_ include VM instances, their types, and disks.

## Projects

Any GCP resources that you allocate and use must belong to a project.

Each GCP project has:

* A project name, which you provide.
* A project ID, which you can provide or GCP can provide for you.
* A project number, which GCP provides.

Each project ID is unique across GCP. Once you have created a project, you can delete the project but its ID can never be used again.

A project serves as a namespace. This means every resource within each project must have a unique name, but you can usually reuse resource names if they are in separate projects. Some resource names must be globally unique.

### Ways to interact with the services <a id="ways_to_interact_with_the_services"></a>

GCP gives you three basic ways to interact with the services and resources.

#### Google Cloud Platform Console <a id="google-cloud-platform-console"></a>

#### Command-line interface <a id="command-line_interface"></a>

 GCP also provides [Cloud Shell](https://cloud.google.com/shell/docs/features), a browser-based, interactive shell environment for GCP. Cloud Shell provides:

* A temporary Compute Engine virtual machine instance.
* Command-line access to the instance from a web browser.
* A built-in code editor.
* 5 GB of persistent disk storage.
* Pre-installed Google Cloud SDK and other tools.
* Language support for Java, Go, Python, Node.js, PHP, Ruby and .NET.
* Web preview functionality.
* Built-in authorization for access to GCP Console projects and resources.

#### Client libraries <a id="client_libraries"></a>

GCP client libraries expose APIs for two main purposes:

* _App APIs_ provide access to services. App APIs are optimized for supported languages, such as Node.js and Python.
* _Admin APIs_ offer functionality for resource management. 

![](../.gitbook/assets/image%20%287%29.png)

