---
description: >-
  Stackdriver Logging allows you to store, search, analyze, monitor, and alert
  on log data and events from Google Cloud Platform and Amazon Web Services.
---

# Stackdriver Logging

### Projects <a id="projects"></a>

Logs are associated primarily with GCP projects, although other resources, such as organizations, folders, and billing accounts, can also have logs. The Logs Viewer shows only the logs from one project, but using the API, you can read log entries across multiple resources.

### Log entries <a id="log_entries"></a>

A log entry records status or an event. The entry might be created by GCP services, AWS services, third-party applications, or your own applications. The "message" the log entry carries is called the payload, and it can be a simple string or structured data.

Your project receives log entries when you begin to use the services that routinely produce log entries, like Compute Engine or BigQuery. You also get log entries when you connect Stackdriver to AWS, when you install the Logging agent on your VM instances, and when you call the [entries.write](https://cloud.google.com/logging/docs/api/reference/rest/v2/entries/write) method in the API.

### Logs <a id="logs"></a>

A log is a named collection of log entries within a GCP resource. Each log entry includes the name of its log. A log name can be a simple identifier, like `syslog`, or a structured name including the log's author, like`compute.googleapis.com/activity`. Logs exist only if they have log entries.

### Retention period <a id="retention_period"></a>

Log entries are held in Stackdriver Logging for a limited time known as the retention period. After that, the entries are deleted. If you want to keep your log entries longer, [export them](https://cloud.google.com/logging/docs/basic-concepts#sinks) outside of Stackdriver Logging.

The retention periods for different types of logs are listed in the Logging [Quota Policy](https://cloud.google.com/logging/quotas).

### Monitored resources <a id="monitored-resources"></a>

Each log entry indicates where it came from by including the name of a monitored resource. Examples are individual Compute Engine VM instances, individual Amazon EC2 VM instances, database instances, and so on. For a complete listing of monitored resource types, see [Monitored Resources and Services](https://cloud.google.com/logging/docs/api/v2/resource-list).

### Filters <a id="filters"></a>

An [advanced logs filter](https://cloud.google.com/logging/docs/view/advanced_filters) is an expression in the Logging filter language. It is used in the Logs Viewer and the Stackdriver Logging API to select log entries, such as those from a particular VM instance or those arriving in a particular time period with a particular severity level.

### Exporting logs using sinks <a id="sinks"></a>

Log entries received by Logging can be exported to Cloud Storage buckets, BigQuery datasets, and Cloud Pub/Sub topics. You export logs by configuring log sinks, which then continue to export log entries as they arrive in Logging. A sink includes a destination and a filter that selects the log entries to export.

### Logs-based metrics <a id="logs-based_metrics"></a>

[Metrics](https://cloud.google.com/monitoring/api/v3/metrics) are a feature of Stackdriver Monitoring. A logs-based metric is a metric whose value is the number of log entries that match a [filter](https://cloud.google.com/logging/docs/view/advanced_filters) that you specify.

### Audit logs <a id="audit_logs"></a>

An audit log is a permanent log written by a GCP service to record administrative or user actions. Audit logs appear in the Logs Viewer alongside other logs. For more information, see [Audit Logs](https://cloud.google.com/logging/docs/audit/).

### Access control <a id="access_control"></a>

The ability to read Logging logs is controlled by granting Cloud Identity and Access Management permissions to members.

Most logs can be read by any member with the Cloud IAM **Viewer** role. [Data Access audit logs](https://cloud.google.com/logging/docs/audit#data-access), except BigQuery Data Access audit logs, are the only "private logs"; to read these, the member requires either the Cloud IAM Owner role or other special permissions.



