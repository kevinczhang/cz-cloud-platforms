---
description: >-
  Cloud Firestore in Datastore mode is a NoSQL document database built for
  automatic scaling, high performance, and ease of application development.
---

# Cloud Datastore

Good for:

* Semistructured application data
* Hierarchical data
* Durable key-value data

Common workloads:

* User profiles
* Product catalogs
* Game state

Cloud Firestore in Datastore mode automatically encrypts all data before it is written to disk. There is no setup or configuration required and no need to modify the way you access the service. The data is automatically and transparently decrypted when read by an authorized user.

### Comparison with traditional databases <a id="comparison_with_traditional_databases"></a>

| Concept | Cloud Datastore | Cloud Firestore | Relational database |
| :--- | :--- | :--- | :--- |
| Category of object | Kind | Collection group | Table |
| One object | Entity | Document | Row |
| Individual data for an object | Property | Field | Column |
| Unique ID for an object | Key | Document ID | Primary key |

### Using transactions <a id="using_transactions"></a>

Transactions have a maximum duration of 60 seconds with a 10 second idle expiration time after 30 seconds.

An operation may fail when:

* Too many concurrent modifications are attempted on the same [entity group](https://cloud.google.com/datastore/docs/concepts/entities#entity_groups).
* The transaction exceeds a resource limit.
* Cloud Datastore encounters an internal error.

In all these cases, the Cloud Datastore API returns an error.

### Consistency levels <a id="consistency_levels"></a>

Datastore queries can deliver their results at either of two consistency levels:

* [_Strongly consistent_](https://en.wikipedia.org/wiki/Strong_consistency) queries guarantee the most up-to-date results, but may take longer to complete or may not be supported in certain cases. \(Look up by Row key\)
* [_Eventually consistent_](https://en.wikipedia.org/wiki/Eventual_consistency) queries generally run faster, but may occasionally return stale results. \(Look up by query\)

