---
description: >-
  gsutil is a Python application that lets you access Cloud Storage from the
  command line.
---

# gsutil Tool

You can use gsutil to do a wide range of bucket and object management tasks, including:

* Creating and deleting buckets.
* Uploading, downloading, and deleting objects.
* Listing buckets and objects.
* Moving, copying, and renaming objects.
* Editing object and bucket ACLs.

## ls - List providers, buckets, or objects

If you run gsutil ls without URLs, it lists all of the Cloud Storage buckets under your default project ID:

```text
gsutil ls
```

If you specify object URLs, gsutil ls will list the specified objects. For example:

```text
gsutil ls gs://bucket/*.txt
```

will list all files whose name matches the above wildcard at the top level of the bucket.

## cp - Copy files and objects

Copy all text files from the local directory to a bucket you could do:

```text
gsutil cp *.txt gs://my-bucket
```

Similarly, you can download text files from a bucket by doing:

```text
gsutil cp gs://my-bucket/*.txt .
```

## mv - Move/rename objects and/or subdirectories

To move all objects from a bucket to a local directory you could use:

```text
gsutil mv gs://my_bucket/* dir
```

Similarly, to move all objects from a local directory to a bucket you could use:

```text
gsutil mv ./dir gs://my_bucket
```

You can use the gsutil mv command to rename subdirectories. For example, the command:

```text
gsutil mv gs://my_bucket/olddir gs://my_bucket/newdir
```

## rb - Remove buckets

```text
gsutil rb [-f] url...
```

The rb command deletes a bucket. Buckets must be empty before you can delete them.

## rm - Remove objects

The gsutil rm command removes objects and/or buckets. For example, the command:

```text
gsutil rm gs://bucket/subdir/*
```

will remove all objects in gs://bucket/subdir, but not in any of its sub-directories. In contrast:

```text
gsutil rm gs://bucket/subdir/**
```

will remove all objects under gs://bucket/subdir or any of its subdirectories.

## web - Set a main page and/or error page for one or more buckets

```text
gsutil web set [-m main_page_suffix] [-e error_page] bucket_url...
gsutil web get bucket_url
```

The Website Configuration feature enables you to configure a Cloud Storage bucket to behave like a static website. This means requests made via a domain-named bucket aliased using a Domain Name System "CNAME" to c.storage.googleapis.com will work like any other website, i.e., a GET to the bucket will serve the configured "main" page instead of the usual bucket listing and a GET for a non-existent object will serve the configured error page.

