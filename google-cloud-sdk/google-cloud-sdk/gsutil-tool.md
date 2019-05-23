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

### Syntax for accessing resources <a id="syntax"></a>

gsutil uses the prefix `gs://` to indicate a resource in Cloud Storage:

```text
gs://[BUCKET_NAME]/[OBJECT_NAME]
```

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

## acl - Get, set, or change bucket and/or object ACLs

### Get <a id="get"></a>

The "acl get" command gets the ACL text for a bucket or object, which you can save and edit for the acl set command.

### Set <a id="set"></a>

The "acl set" command allows you to set an Access Control List on one or more buckets and objects. The simplest way to use it is to specify one of the canned ACLs, e.g.,:

```text
gsutil acl set private gs://bucket
```

Make changes to acl.txt such as adding an additional grant, then:

```text
gsutil acl set acl.txt gs://cats/file.txt
```

### Ch <a id="ch"></a>

The "acl ch" \(or "acl change"\) command updates access control lists

Grant anyone on the internet READ access to the object example-object:

```text
gsutil acl ch -u AllUsers:R gs://example-bucket/example-object
```

Grant the user [john.doe@example.com](mailto:john.doe%40example.com) WRITE access to the bucket example-bucket:

```text
gsutil acl ch -u john.doe@example.com:WRITE gs://example-bucket
```

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

## cors - Get or set a CORS JSON document for one or more buckets

```text
gsutil cors set cors-json-file url...
gsutil cors get url
```

## iam - Get, set, or change bucket and/or object IAM permissions



```text
gsutil iam set [-afRr] [-e <etag>] file url ...
  gsutil iam get url
  gsutil iam ch [-fRr] binding ... url

  where each binding is of the form:

      [-d] ("user"|"serviceAccount"|"domain"|"group"):id:role[,...]
      [-d] ("allUsers"|"allAuthenticatedUsers"):role[,...]
      -d ("user"|"serviceAccount"|"domain"|"group"):id
      -d ("allUsers"|"allAuthenticatedUsers")

Note: The ``iam ch`` command does not support changing IAM policies with
bindings that contain conditions. As such, ``iam ch`` cannot be used to add
conditions to a policy or to change the policy of a resource that already
contains conditions. See additional details below.

Note: The ``gsutil iam`` command disallows using project convenience groups
(projectOwner, projectEditor, projectViewer) as the first segment of a binding
because these groups go against the principle of least privilege.
```

### Get <a id="get"></a>

The `iam get` command gets the IAM policy for a bucket or object, which you can save and edit for use with the `iamset` command.

For example:

```text
gsutil iam get gs://example > bucket_iam.txt
gsutil iam get gs://example/important.txt > object_iam.txt
```

### Set <a id="set"></a>

The `iam set` command sets the IAM policy for one or more buckets and / or objects. It overwrites the current IAM policy that exists on a bucket \(or object\) with the policy specified in the input file. The `iam set` command takes as input a file with an IAM policy in the format of the output generated by `iam get`.

### Ch <a id="ch"></a>

The `iam ch` command incrementally updates IAM policies. 

### Ch Examples <a id="ch-examples"></a>

Examples for the `ch` sub-command:

To grant a single role to a single member for some targets:

```text
gsutil iam ch user:john.doe@example.com:objectCreator gs://ex-bucket
```

To make a bucket's objects publicly readable:

```text
gsutil iam ch allUsers:objectViewer gs://ex-bucket
```

To grant multiple bindings to a bucket:

```text
gsutil iam ch user:john.doe@example.com:objectCreator \
              domain:www.my-domain.org:objectViewer gs://ex-bucket
```

To specify more than one role for a particular member:

```text
gsutil iam ch user:john.doe@example.com:objectCreator,objectViewer \
              gs://ex-bucket
```

To specify a custom role for a particular member:

```text
gsutil iam ch user:john.doe@example.com:roles/customRoleName gs://ex-bucket
```

To apply a grant and simultaneously remove a binding to a bucket:

```text
gsutil iam ch -d group:readers@example.com:legacyBucketReader \
              group:viewers@example.com:objectViewer gs://ex-bucket
```

To remove a user from all roles on a bucket:

```text
gsutil iam ch -d user:john.doe@example.com gs://ex-bucket
```

