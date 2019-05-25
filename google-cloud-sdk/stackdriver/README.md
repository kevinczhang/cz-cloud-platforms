---
description: >-
  Cloud Platform provides tools for logging and monitoring so you can keep track
  of the performance and availability of your resources and applications.
---

# Stackdriver

## Stackdriver Monitoring

Stackdriver Monitoring provides dashboards and alerts for your applications that run on Cloud Platform. You configure Stackdriver Monitoring using the [Stackdriver Monitoring Console](https://app.google.stackdriver.com/). Review performance metrics for cloud services, Compute Engine instances, and common open source servers such as MongoDB, Apache, Nginx, and Elasticsearch. You can use the Stackdriver Monitoring API to retrieve monitoring data and create custom metrics.

## Stackdriver Logging

Stackdriver Logging collects and stores logs from applications and services running on Cloud Platform. You can use Stackdriver Logging with App Engine or Compute Engine. The [Logs Viewer](https://cloud.google.com/logging/docs/view/logs_viewer) in the GCP Console lets you see your logs. You can export your logs to Cloud Storage, BigQuery, and Cloud Pub/Sub so you can process them more easily. The Stackdriver Logging Agent enables you to integrate third-party logs.

## Debugging, tracing, and analysis

[Stackdriver Debugger](https://cloud.google.com/debugger/) lets you inspect the state of your Java application running on App Engine or Compute Engine at any code location, without stopping the app or slowing it down. The debugger makes it easier to view the application state without adding logging statements. You can use Stackdriver Debugger with any deployment of your application, including test, development, and production.

[Stackdriver Trace](https://cloud.google.com/trace/) enables you to view the remote procedure calls \(RPCs\) invoked by your App Engine application and to view and analyze the time taken to complete each RPC. You can use Stackdriver Trace to create and view analysis reports that show the latency distribution of requests to your application. You can also compare performance of two sets of requests. For example, you can compare the performance of your application before and after a release by comparing the traces for requests received.

