---
description: >-
  The cbt tool is a command-line interface for performing several different
  operations on Cloud Bigtable.
---

# cbt

It is written in [Go](https://golang.org/) using the [Go client library for Cloud Bigtable](https://cloud.google.com/bigtable/docs/reference/libraries). Source code for the `cbt` tool is available in the GitHub repository[GoogleCloudPlatform/google-cloud-go](https://github.com/GoogleCloudPlatform/google-cloud-go/tree/master/bigtable/cmd/cbt). This repository is a mirror of [code.googlesource.com/gocloud](https://code.googlesource.com/gocloud/+/master/bigtable/cmd/cbt/).

Configure `cbt` to use your project and instance by creating a `.cbtrc` file, replacing `[PROJECT_ID]` with the project ID in which you created your Cloud Bigtable instance:

```text
echo project = [PROJECT_ID] > ~/.cbtrc
echo instance = quickstart-instance >> ~/.cbtrc
```

### Read and write data <a id="read-write"></a>

Cloud Bigtable stores data in _tables_, which contain _rows_. Each row is identified by a _row key_.

Data in a row is organized into _column families_, or groups of columns. A _column qualifier_ identifies a single column within a column family.

A _cell_ is the intersection of a row and a column. Each cell can contain multiple _versions_ of a value.

1. Create a table named `my-table`.

   ```text
   cbt createtable my-table
   ```

2. List your tables:

   ```text
   cbt ls
   ```

   The command displays output similar to the following:

   ```text
   my-table
   ```

3. Add one column family named `cf1`:

   ```text
   cbt createfamily my-table cf1
   ```

4. List your column families:

   ```text
   cbt ls my-table
   ```

   The command displays output similar to the following:

   ```text
   Family Name     GC Policy
   -----------     ---------
   cf1             <never>
   ```

5. Put the value `test-value` in the row `r1`, using the column family `cf1` and the column qualifier `c1`:

   ```text
   cbt set my-table r1 cf1:c1=test-value
   ```

6. Use the `cbt read` command to read the data you added to the table:

   ```text
   cbt read my-table
   ```

   The shell displays output similar to the following:

   ```text
   ----------------------------------------
   r1
     cf1:c1                                   @ 2019/03/26-15:05:38.840000
       "test-value"
   ```

7. Delete the table `my-table`:

   ```text
   cbt deletetable my-table
   ```

