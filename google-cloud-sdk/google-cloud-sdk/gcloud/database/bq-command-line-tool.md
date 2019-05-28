---
description: 'bq is a python-based, command-line tool for BigQuery.'
---

# bq Tool

`bq` supports two kinds of flags — global flags and command flags. They should be used in the order shown here:

```text
bq --global_flag [ARGUMENT] bq_command --command-specific_flag [ARGUMENT]
```

* **Global flags** \(or common flags\) can be used in all commands.
* **Command-specific flags** apply to a specific command.

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



