---
description: 'bq is a python-based, command-line tool for BigQuery.'
---

# bq for bigQuery

## Basic syntax for bq

```text
bq --global_flag [ARGUMENT] bq_command --command-specific_flag [ARGUMENT]
```

`bq` supports two kinds of flags — global flags and command flags. They should be used in the order shown here:

* **Global flags** \(or common flags\) can be used in all commands.
  * **`--format`**

    Specifies the format of the command's output including: pretty, sparse, prettyjson, json, csv

  * **`--apilog`**Log all API requests and responses to the file specified by this flag. You can also use `stdout` and `stderr`. Specifying the empty string \(`''`\) will direct to `stdout`.
  * **`--debug_mode`**Show tracebacks on Python exceptions. The default value is `false`.
  * **`--headless`**

    Specifies whether to run the `bq` session without user interaction. 

  * **`--quiet` or `-q`**

    If set to `true`, ignore status updates while jobs are running. The default value is `false`.

  * **`--synchronous_mode` or `-sync`**

    If set to `true`, wait for the command to complete before returning, and use the job completion status as the error code. If set to `false`, the job is created, and successful completion status is used for the error code. The default value is `true`.
* **Command-specific flags** apply to a specific command.

## CRUD operations

#### `bq cp:` The `cp` command is used to copy tables.  <a id="bq_cp"></a>

#### bq extract:  The `extract` command is used to export table data to Google Cloud Storage. <a id="bq_extract"></a>

#### bq head: The `head` command displays rows in a table. <a id="bq_head"></a>

#### bq insert: The `insert` command allows you to insert rows of newline-delimited JSON formatted data using the streaming buffer. This command is intended for testing purposes only. To stream data into BigQuery, use the [`insertAll`](https://cloud.google.com/bigquery/docs/reference/rest/v2/tabledata/insertAll) API method. <a id="bq_insert"></a>

#### bq load: The `load` command loads data into a table. <a id="bq_load"></a>

#### bq ls: The `ls` command lists objects in a collection. <a id="bq_ls"></a>

#### bq mk: The `mk` command creates a dataset, table, view, or transfer configuration. <a id="bq_mk"></a>

#### bq mkdef: The `mkdef` command creates a table definition in JSON format for data stored in Google Cloud Storage or Google Drive. <a id="bq_mkdef"></a>

#### bq partition: The `partition` command is used to convert date-named tables \(ending in \[YYYYmmdd\]\) into partitioned tables. <a id="bq_partition"></a>

#### bq query: The `query` command creates a query job that runs the supplied SQL query. <a id="bq_query"></a>

#### bq rm: The `rm` command deletes a dataset, table, view, model, or transfer configuration. <a id="bq_rm"></a>

#### bq show: The `show` command displays information about an object. <a id="bq_rm"></a>

#### bq update: The `update` command updates a dataset, table, view, model, or transfer configuration. bq wait: The `wait` command waits some number of seconds for a job to finish. <a id="bq_rm"></a>

### Examine a table <a id="examine_a_table"></a>

To examine the schema of a specific table, run

```text
bq show projectId:datasetId.tableId
```

### Run a query <a id="run_a_query"></a>

To run a query, run the command `bq query "[SQL_STATEMENT]"`.

* Escape any quotation marks inside the `[SQL_STATEMENT]` with a `\` mark, or
* Use a different quotation mark type than the surrounding marks \(`"` versus `'`\).

### Create a new dataset

1. Use the `bq ls` command to see whether your default project has any existing datasets.
2. Use the `bq mk` command to create a new dataset named `babynames` in your default project. 
3. The `bq load` command creates or updates a table and loads data in a single step.

Run the `bq load` command to load your source file into a new table called `names2010` in the `babynames` dataset you created above. By default, this runs synchronously, and will take a few seconds to complete.

```text
bq load babynames.names2010 yob2010.txt name:string,gender:string,count:integer
```

The `bq load` command arguments:

* datasetID: `babynames`
* tableID: `names2010`
* source: `yob2010.txt`
* schema: `name:string,gender:string,count:integer`

## Listing datasets

To list all datasets in a project, excluding anonymous datasets, use the `--datasets` flag or the `-d` shortcut. This flag is optional. By default, anonymous datasets are not listed.

```text
bq ls --format=prettyjson --project_id [PROJECT_ID]
```

Where:

* `[PROJECT_ID]` is the name of your project.

 A dataset is contained within a specific [project](https://cloud.google.com/bigquery/docs/projects). Datasets are top-level containers that are used to organize and control access to your [tables](https://cloud.google.com/bigquery/docs/tables) and [views](https://cloud.google.com/bigquery/docs/views). A table or view must belong to a dataset, so you need to create at least one dataset before [loading data into BigQuery](https://cloud.google.com/bigquery/loading-data-into-bigquery).

## Create dataset, table, view or transfer configuration

#### bq mk <a id="bq_mk"></a>

The `mk` command creates a dataset, table, view, or transfer configuration.

```text
bq --location=[LOCATION] mk --dataset --default_table_expiration [INTEGER] --default_partition_expiration [INTEGER2] --description [DESCRIPTION] [PROJECT_ID]:[DATASET]
```

```text
bq mk --table --expiration [INTEGER] --description [DESCRIPTION] --label [KEY:VALUE, KEY:VALUE] [PROJECT_ID]:[DATASET].[TABLE] [SCHEMA]
```



