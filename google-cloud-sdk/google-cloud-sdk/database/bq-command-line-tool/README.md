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



