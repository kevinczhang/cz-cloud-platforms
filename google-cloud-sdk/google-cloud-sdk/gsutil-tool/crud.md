# CRUD

## mb - Make buckets

The mb command creates a new bucket. Cloud Storage has a single namespace, so you are not allowed to create a bucket with a name already in use by another user.

```text
gsutil mb [-b <on|off>] [-c class] [-l location] [-p proj_id]
          [--retention time] url...
```

* `-p`: specify the project with which your bucket will be associated.
* `-c`: specify the default [storage class](https://cloud.google.com/storage/docs/storage-classes) of your bucket.
* `-l`: specify the location of your bucket.

### Bucket Storage Classes <a id="bucket-storage-classes"></a>

You can specify one of the [storage classes](https://cloud.google.com/storage/docs/storage-classes) for a bucket with the -c option.

```text
gsutil mb -c nearline gs://some-bucket
```

### Bucket Locations <a id="bucket-locations"></a>

You can specify one of the [available locations](https://cloud.google.com/storage/docs/locations) for a bucket with the -l option.

```text
gsutil mb -l asia gs://some-bucket

gsutil mb -c regional -l us-east1 gs://some-bucket
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

