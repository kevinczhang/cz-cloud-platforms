# jobs

When a job is submitted, it can be in one of three states:

* `PENDING` — scheduled
* `RUNNING`
* `DONE` — reported as `SUCCESS` or `FAILURE` \(if the job completed with errors\)

## Viewing job data

If you grant an account the `bigquery.admin` role, the user can view all job data in the project no matter who submitted the job.

The following roles are granted `bigquery.jobs.get` permissions for self-created jobs. These users can only view job data for jobs they submit:

* [`bigquery.user`](https://cloud.google.com/bigquery/access-control#bigquery.user)
* [`bigquery.jobUser`](https://cloud.google.com/bigquery/access-control#bigquery.jobUser)

### To view information about a job

Issue the `bq show` command with the `-j` flag and the `job_id` parameter. Supply the `--location` flag and set the value to your[location](https://cloud.google.com/bigquery/docs/locations).

The following command requests information about a job:

```text
bq --location=[LOCATION] show -j [JOB_ID]
```

Where:

* `[LOCATION]` is the name of the location where the job runs. For example, if you are using BigQuery in the Tokyo region, set the flag's value to `asia-northeast1`. You can set a default value for the location using the [.bigqueryrc file](https://cloud.google.com/bigquery/docs/bq-command-line-tool#setting_default_values_for_command-line_flags).
* `[JOB_ID]` is the ID of the job.

### To see full job details, enter:

```text
bq --location=US show --format=prettyjson -j myproject:bquijob_123x456_789y123z456c
```

## Listing jobs

Issue the `bq ls` command with one of the following flags:

* `-j` is used to identify jobs as the resource to list.
* `--all` or `-a` lists jobs from all users. To see full \(unredacted\) details for all jobs, you must have `bigquery.jobs.listAll`permissions.
* `--min_creation_time` is used to list jobs after a supplied timestamp value.
* `--max_creation_time` is used ot list jobs before a supplied timestamp value.
* `-n` limits the results. By default, you are limited to 100,000 results.

  ```text
  bq ls -j -a --min_creation_time [INTEGER1] --max_creation_time [INTEGER2] -n [INTEGER3] [PROJECT_ID]
  ```

Where:

* `[INTEGER1]` is an integer that represents a timestamp.
* `[INTEGER2]` is an integer that represents a timestamp.
* `[INTEGER3]` is an integer that indicates the number of jobs returned.
* `[PROJECT_ID]` is the ID of the project that contains the jobs you're listing. If you [set a default project](https://cloud.google.com/sdk/gcloud/reference/config/set), you do not need to provide the `[PROJECT_ID]` parameter.

Examples:

The following command lists all jobs for the current user. Running this command requires `bigquery.jobs.list` permissions.

```text
bq ls -j myproject
```

The following command lists all jobs for all users. Running this command requires `bigquery.jobs.listAll` permissions.

```text
bq ls -j -a myproject
```

The following command lists the 10 most recent jobs in `myproject`:

```text
bq ls -j -a -n 10 myproject
```

The following command lists all jobs submitted before Oct 18, 2018, at 4:04:53 PM. This timestamp \(in milliseconds\) is equivalent to the following integer value: 1539903893000.

```text
bq ls -j --max_creation_time 1539903893000
```

## Cancelling jobs

The following command cancels job `my-project-1234:US.bquijob_123x456_123y123z123c` running in the `US` multi-region location in `my-project-1234` and waits for completion. Because the fully-qualified job ID is used, the location flag is not supplied.

```text
bq cancel my-project-1234:US.bquijob_123x456_123y123z123c
```

The following command cancels job `bquijob_123x456_123y123z123c` running in the `US` multi-region location in `my-project-1234`and waits for completion. Because the short form of the job ID is used, the `--location` flag is supplied.

```text
bq --location=US cancel bquijob_123x456_123y123z123c
```

The following command cancels job `bquijob_123x456_123y123z123c` running in the `US` multi-region location in `my-project-1234`and returns immediately. Because the fully-qualified job ID is used, the `--location` flag is not supplied.

```text
bq --nosync cancel my-project-1234:US.bquijob_123x456_123y123z123c
```



