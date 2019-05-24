# Object Lifecycle Management

The configuration contains a set of rules which apply to current and future objects in the bucket. When an object meets the criteria of one of the rules, Cloud Storage automatically performs a specified action on the object. Here are some example use cases:

* Downgrade the storage class of objects older than 365 days to Coldline Storage.
* Delete objects created before January 1, 2013.
* Keep only the 3 most recent versions of each object in a bucket with versioning enabled.

## Lifecycle actions

If a single object is subject to multiple actions, Cloud Storage performs only one of the actions, and the object will be re-evaluated before any additional actions are taken. A Delete action takes precedence over a SetStorageClass action. If multiple SetStorageClass actions are specified, the action switching to the storage class with the lowest at-rest storage pricing is chosen.

* **Delete**: Delete live and/or archived objects. 
* **SetStorageClass**: Change the [storage class](https://cloud.google.com/storage/docs/storage-classes) of live and/or archived objects. 
  * This action can be applied to both versioned and non-versioned objects. This action supports the following storage class transitions:

    | Original storage class | New storage class |
    | :--- | :--- |
    | Multi-Regional Storage | Nearline Storage Coldline Storage |
    | Regional Storage | Nearline Storage Coldline Storage |
    | Nearline Storage | Coldline Storage |

## Lifecycle conditions

* **Age**: This condition is satisfied when an object reaches the specified age \(in days\). 
* **CreatedBefore**: This condition is satisfied when an object is created before midnight of the specified date in UTC.
* **IsLive**: If the value is `true`, this lifecycle condition matches only live objects; if the value is `false`, it matches only archived objects. For the purposes of this condition, objects in non-versioned buckets are considered live.
* **MatchesStorageClass**: This condition is satisfied when an object in the bucket is stored as the specified storage class.

