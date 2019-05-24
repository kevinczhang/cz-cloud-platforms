---
description: >-
  App Engine flexible environment allows you to customize the runtime and even
  the operating system of your virtual machine using Dockerfiles.
---

# Flexible Environment

* **Runtimes** - The flexible environment includes native support for Java 8 \(with no web-serving framework\), Eclipse Jetty 9, Python 2.7 and Python 3.6, Node.js, Ruby, PHP, .NET core, and Go. Developers can customize these runtimes or provide their own runtime by supplying a custom Docker image or Dockerfile from the open source community.
* **Infrastructure Customization** - Because VM instances in the flexible environment are [Google Compute Engine](https://cloud.google.com/compute/)virtual machines, you can take advantage of custom libraries, use SSH for debugging, and deploy your own Docker containers.
* **Performance** - Take advantage of a wide array of CPU and memory configurations. You can specify how much CPU and memory each instance of your application needs and the flexible environment will provision the necessary infrastructure for you.

App Engine manages your virtual machines, ensuring that:

* Instances are health-checked, healed as necessary, and co-located with other services within the project.
* Critical, backwards compatible updates are automatically applied to the underlying operating system.
* VM instances are automatically located by geographical region according to the settings in your project. Google's management services ensure that all of a project's VM instances are co-located for optimal performance.
* VM instances are restarted on a weekly basis. During restarts Google's management services will apply any necessary operating system and security updates.
* You always have root access to Compute Engine VM instances. SSH access to VM instances in the flexible environment is disabled by default. If you choose, you can enable root access to your app's VM instances.

## Choosing an App Engine environment

## When to choose the standard environment

Application instances run in a [sandbox](https://en.wikipedia.org/wiki/Sandbox_%28computer_security%29), using the runtime environment of a supported language listed below.

Applications that need to deal with rapid scaling.

The standard environment is optimal for applications with the following characteristics:

* Source code is written in **specific versions of the supported programming languages**:
  * Python 2.7, Python 3.7
  * Java 8
  * Node.js 8, and Node.js 10
  * PHP 5.5, and PHP 7.2
  * Go 1.9, Go 1.11, and Go 1.12 \(beta\)
* Intended to **run for free or at very low cost**, where you pay only for what you need and when you need it. For example, your application can scale to 0 instances when there is no traffic.
* Experiences **sudden and extreme spikes of traffic** which require immediate scaling.

## When to choose the flexible environment

Application instances run within Docker containers on Compute Engine virtual machines \(VM\).

Applications that receive consistent traffic, experience regular traffic fluctuations, or meet the parameters for scaling up and down gradually.

The flexible environment is optimal for applications with the following characteristics:

* Source code that is written in a version of any of the supported programming languages:  **Python**, **Java**, **Node.js**, **Go**, **Ruby**, **PHP**, or **.NET**
* Runs in a Docker container that includes a custom runtime or source code written in **other programming languages**.
* Uses or depends on frameworks that include **native code**.
* Accesses the resources or services of your Google Cloud Platform project that reside in the **Compute Engine network**.

