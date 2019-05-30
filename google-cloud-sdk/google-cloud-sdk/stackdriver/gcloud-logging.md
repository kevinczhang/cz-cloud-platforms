---
description: Manage Stackdriver Logging.
---

# gcloud logging

 `gcloud logging` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/logging/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/logging/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/logging/#GCLOUD-WIDE-FLAGS) `…`\]

 `GROUP` is one of the following:

* [`logs`](https://cloud.google.com/sdk/gcloud/reference/logging/logs)Manages your project's logs.
* [`metrics`](https://cloud.google.com/sdk/gcloud/reference/logging/metrics)Manages logs-based metrics.
* [`resource-descriptors`](https://cloud.google.com/sdk/gcloud/reference/logging/resource-descriptors)Get information about resource descriptors.
* [`sinks`](https://cloud.google.com/sdk/gcloud/reference/logging/sinks)Manages sinks used to export logs.

 `COMMAND` is one of the following:

* [`read`](https://cloud.google.com/sdk/gcloud/reference/logging/read)Read log entries.
* [`write`](https://cloud.google.com/sdk/gcloud/reference/logging/write)Write a log entry.

## Log-based metric

 To create a metric that counts the number of log entries with a severity level higher than WARNING, run:

```text
  $ gcloud logging metrics create high_severity_count \
      --description="Number of high severity log entries" \
      --log-filter="severity > WARNING"
```

## Sink

 To export all Google Compute Engine logs to BigQuery, run:

```text
  $ gcloud logging sinks create my-bq-sink \
      bigquery.googleapis.com/projects/my-project/datasets/\
  my_dataset --log-filter='resource.type="gce_instance"'
```

To export "syslog" from App Engine Flexible to Cloud Storage, run:

```text
  $ gcloud logging sinks create my-gcs-sink \
      storage.googleapis.com/my-bucket \
      --log-filter='logName="projects/my-project/appengine.googleapis.\
  com%2Fsyslog"'
```

To export Google App Engine logs with ERROR severity, run:

```text
  $ gcloud logging sinks create my-error-logs \
      bigquery.googleapis.com/projects/my-project/datasets/\
  my_dataset --log-filter='resource.type="gae_app" AND severity=ERROR'
```

