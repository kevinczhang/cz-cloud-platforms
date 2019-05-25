---
description: >-
  To use Monitoring, you must have the appropriate Cloud IAM permissions granted
  on the Workspace.
---

# Stackdriver Monitoring

## Workspace 

{% hint style="info" %}
 **Note:** "Stackdriver accounts" have been renamed "Workspaces" to reflect their use as a "single pane of glass" through which you view resources from multiple Google Cloud Platform \(GCP\) projects and Amazon Web Services \(AWS\) accounts. There is no change in their functionality.
{% endhint %}

To use Monitoring, you must have a Workspace.

#### Create Workspace permissions <a id="create-roles"></a>

To create a Workspace for an existing GCP project you must have one of the following Cloud IAM roles on that project:

* Project Owner
* Monitoring Editor
* Monitoring Admin
* Stackdriver Accounts Editor

 **Note:** A Workspace's _host project_ is the project used to create the Workspace.

A Workspace is a tool for monitoring resources contained in one or more GCP projects or AWS accounts. Each Workspace can have between 1 and 100 **monitored projects.** You can have as many Workspaces as you wish, but GCP projects and AWS accounts can't be monitored by more than one Workspace.

### The hosting project <a id="host-project"></a>

The first monitored GCP project in a Workspace is called the **hosting project**, and it must be specified when you create the Workspace. The name of that project becomes the name of your Workspace.

If you plan to monitor more than just your hosting project, then the best practice is to use a new, empty GCP project to host the Workspace and then to add the projects and AWS accounts you want to monitor to your Workspace.

### To install the agent, ensure that you have one of the following:

* A [supported VM instance](https://cloud.google.com/monitoring/agent/#supported_vms) in a Google Cloud Platform \(GCP\) project or Amazon Web Services \(AWS\) account.
  * A minimum of 250 MiB of resident \(RSS\) memory is recommended to run the Monitoring agent.
* A [Workspace](https://cloud.google.com/monitoring/accounts/) monitoring the GCP project or AWS account containing the VM instance.
* Credentials on the VM instance that authorize communication with Stackdriver.
  * GCP VM instances generally have the correct credentials by default.
  * For AWS instances, you must [install authorization credentials](https://cloud.google.com/monitoring/agent/install-agent#private_key_authorization) on your VMs before installing the agent.

## Creating uptime checks

### Basic options

1. **Title**: A name to identify your check. For example, `Example.com uptime check`.
2. **Check Type**: Select an **HTTP**, **HTTPS**, or **TCP** protocol.

   If you select HTTPS, the service attempts to connect over HTTPS, but doesn't validate the SSL certificate. For example, expired or self-signed certificates won't cause a check to fail.

3. **Resource type**: Choose one of the following resource types:
   * **App Engine**: App Engine applications \(modules\).
   * **Elastic Load Balancer**: AWS load balancer.
   * **Instance**: Compute Engine or AWS EC2 instances. In the API, this is split into `gce_instance` and `aws_ec2_instance`.
   * **URL**: Any IPv4 address or hostname. Path and port are entered separately.
4. Complete the connection information, depending on your check type and resource type:
   * **Applies to** \(App Engine, ELB, or Instance\): You can apply your uptime check to a single resource or to a group of resources, such as **All instances**. If you choose a single resource, pick one from your existing resources listed in the menu. If you use the API, fill in the monitored resource with the required resource labels, as described in the [Monitored resource list](https://cloud.google.com/monitoring/api/resources).
   * **Module** \(App Engine\): Specify your application module.
   * **Hostname** \(All except for App Engine\): Specify your service's host name. For example, enter `example.com`.
   * **Path** \(HTTP, HTTPS\): Enter a path within your host or resource or use the default path. For example, to probe `example.com`, leave this field blank. To probe `example.com/tester`, enter `/tester`. Do not include the prefix `example.com`. In the API, leave this field blank to use the default value, `/`.
   * **Port** \(HTTP, HTTPS, TCP\): Choose a port for the connection.
     * For HTTP and HTTPS checks, this option is under **Advanced Options**.
     * In the API, leave this field blank to use the default value: 80 for TCP or HTTP checks, and 443 for HTTPS checks.
   * **Response content contains the text** \(HTTP, HTTPS, TCP\): Fill in a string \(max 1024 bytes\) whose presence in the check response indicates success. The check will fail if the string does not appear anywhere in the response.
     * For HTTP and HTTPS check, this field appears under **Advanced Options**.
     * In the API, this is the [`ContentMatcher`](https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.uptimeCheckConfigs#ContentMatcher) object.
5. **Check every**: **1**, **5**, **10**, or **15** minutes. For example, if you select 5 minutes, each geographic location attempts to reach your service once in every 5 minute period. Using the default 6 locations, and checking every 5 minutes, your service sees an average of 1.2 requests per minute. Checking every 1 minute, your service sees an average of 6 requests per minute.

If you want to be notified of uptime failures, create an alerting policy for your new uptime check.

## Alerting

To create an alerting policy, you must describe the circumstances under which you want to be alerted and how you want to be notified.

You can create and manage **alerting policies** with the Stackdriver Monitoring console, the [Stackdriver Monitoring API](https://cloud.google.com/monitoring/api/v3/), and [Cloud SDK](https://cloud.google.com/sdk/gcloud/reference/alpha/monitoring/policies).

Each policy specifies the following:

* **Conditions** that identify an unhealthy state for a resource or a group of resources.
* Optional **notifications** sent through email, SMS, or other channels to let your support team know a resource is unhealthy.
* Optional **documentation** that can be included in some types of notifications to help your support team resolve the issue.

