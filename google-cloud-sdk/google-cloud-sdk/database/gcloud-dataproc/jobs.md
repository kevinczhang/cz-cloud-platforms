---
description: gcloud dataproc jobs
---

# jobs

Submit and manage Google Cloud Dataproc jobs.

 `GROUP` is one of the following:[`submit`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit)Submit Google Cloud Dataproc jobs to execute on a cluster.

 `COMMAND` is one of the following:

* [`delete`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/delete)Delete the record of an inactive job.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/describe)View the details of a job.
* [`get-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/get-iam-policy)Get IAM policy for a job.
* [`kill`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/kill)Kill an active job.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/list)List jobs in a project.
* [`set-iam-policy`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/set-iam-policy)Set IAM policy for a job.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/update)Update the labels for a job.
* [`wait`](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/wait)View the output of a job as it runs or after it completes.

## EXAMPLES

To learn about the types of jobs that can be submitted, run:

```text
  $ gcloud dataproc jobs submit
```

To view the output of a job as it runs, run:

```text
  $ gcloud dataproc jobs wait job_id
```

To cancel an active job, run:

```text
  $ gcloud dataproc jobs kill job_id
```

To view the details of a job, run:

```text
  $ gcloud dataproc jobs describe job_id
```

To see the list of all jobs, run:

```text
  $ gcloud dataproc jobs list
```

To delete the record of an inactive job, run:

```text
  $ gcloud dataproc jobs delete job_id
```

