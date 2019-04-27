# Flexible Environment

## Choosing an App Engine environment

#### When to choose the standard environment

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

#### When to choose the flexible environment

Application instances run within Docker containers on Compute Engine virtual machines \(VM\).

Applications that receive consistent traffic, experience regular traffic fluctuations, or meet the parameters for scaling up and down gradually.

The flexible environment is optimal for applications with the following characteristics:

* Source code that is written in a version of any of the supported programming languages:  **Python**, **Java**, **Node.js**, **Go**, **Ruby**, **PHP**, or **.NET**
* Runs in a Docker container that includes a custom runtime or source code written in **other programming languages**.
* Uses or depends on frameworks that include **native code**.
* Accesses the resources or services of your Google Cloud Platform project that reside in the **Compute Engine network**.

