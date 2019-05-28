---
description: >-
  gsutil is a Python application that lets you access Cloud Storage from the
  command line.
---

# gsutil for cloudStorage

You can use gsutil to do a wide range of bucket and object management tasks, including:

* Creating and deleting buckets.
* Uploading, downloading, and deleting objects.
* Listing buckets and objects.
* Moving, copying, and renaming objects.
* Editing object and bucket ACLs.

### Syntax for accessing resources <a id="syntax"></a>

gsutil uses the prefix `gs://` to indicate a resource in Cloud Storage:

```text
gs://[BUCKET_NAME]/[OBJECT_NAME]
```

## Built-in help

gsutil contains thorough built-in help about every command as well as a number of topics, which you can get by running:

```text
gsutil help
```

This command outputs a list of all commands and available help topics, and you can then get detailed help for each command or topic. For example, you can get help about the `gsutil cp` command by running:

```text
gsutil help cp
```

To get information about gsutil top-level command-line options, use:

```text
gsutil help options
```

To get information about your gsutil installation, use:

```text
gsutil version -l
```

## 

## 

