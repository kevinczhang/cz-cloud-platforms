# Common operations

## Bucket operations

#### To create a new storage bucket:

```text
  gsutil mb -p [PROJECT_NAME] -c [STORAGE_CLASS] -l [BUCKET_LOCATION] gs://[BUCKET_NAME]/
```

* `-p`: specify the project with which your bucket will be associated.
* `-c`: specify the default [storage class](https://cloud.google.com/storage/docs/storage-classes) of your bucket.
* `-l`: specify the location of your bucket.

#### To list the buckets in a project:

```text
gsutil ls
```

#### To determine the size of a bucket:

```text
gsutil du -s gs://[BUCKET_NAME]/
```

#### To display the geographic [location](https://cloud.google.com/storage/docs/locations) and default [storage class](https://cloud.google.com/storage/docs/storage-classes) of a bucket:

```text
gsutil ls -L -b gs://[BUCKET_NAME]/
```

#### To change the default storage class of an existing bucket:

```text
gsutil defstorageclass set [STORAGE_CLASS] gs://[BUCKET_NAME]
```

#### Copy files from your old bucket to your new bucket

```text
gsutil cp -r gs://[SOURCE_BUCKET]/* gs://[DESTINATION_BUCKET]
```

#### Delete the files from your old bucket

```text
gsutil rm -r gs://[SOURCE_BUCKET]
```

Or, to delete the files but keep the source bucket:

```text
gsutil rm -a gs://[SOURCE_BUCKET]/**
```

## Objects operations

#### Use the [`gsutil cp`](https://cloud.google.com/storage/docs/gsutil/commands/cp) command, replacing `[VALUES_IN_BRACKETS]` with the appropriate values:

```text
gsutil cp [LOCAL_OBJECT_LOCATION] gs://[DESTINATION_BUCKET_NAME]/
```

#### Use the [`gsutil ls`](https://cloud.google.com/storage/docs/gsutil/commands/ls) command with the `-r` flag, replacing `[VALUES_IN_BRACKETS]` with the appropriate values:

```text
gsutil ls -r gs://[BUCKET_NAME]/**
```

or

```text
gsutil ls -r gs://[BUCKET_NAME]/[PREFIX]**
```

#### Use the [`gsutil cp`](https://cloud.google.com/storage/docs/gsutil/commands/cp) command, replacing `[VALUES_IN_BRACKETS]` with the appropriate values:

```text
gsutil cp gs://[BUCKET_NAME]/[OBJECT_NAME] [OBJECT_DESTINATION]
```

#### To rename an existing object in one of your Cloud Storage buckets:

```text
gsutil mv gs://[BUCKET_NAME]/[OLD_OBJECT_NAME] gs://[BUCKET_NAME]/[NEW_OBJECT_NAME]
```

#### To copy an object in one of your Cloud Storage buckets:

```text
gsutil cp gs://[SOURCE_BUCKET_NAME]/[SOURCE_OBJECT_NAME] gs://[DESTINATION_BUCKET_NAME]/[NAME_OF_COPY]
```

#### To move an object in Cloud Storage:

```text
gsutil mv gs://[SOURCE_BUCKET_NAME]/[SOURCE_OBJECT_NAME] gs://[DESTINATION_BUCKET_NAME]/[DESTINATION_OBJECT_NAME]
```

#### Changing object storage classes

```text
gsutil rewrite -s [STORAGE_CLASS] gs://[PATH_TO_OBJECT]
```

#### **To view the metadata associated with an object:**

```text
gsutil ls -L  gs://[BUCKET_NAME]/[OBJECT_NAME]
```

**To edit the metadata associated with an object:**

```text
gsutil setmeta -h "[METADATA_KEY]:[METADATA_VALUE]" gs://[BUCKET_NAME]/[OBJECT_NAME]
```

#### Use the [`gsutil rm`](https://cloud.google.com/storage/docs/gsutil/commands/rm) command, replacing `[VALUES_IN_BRACKETS]` with the appropriate values:

```text
gsutil rm gs://[BUCKET_NAME]/[OBJECT_NAME]
```



