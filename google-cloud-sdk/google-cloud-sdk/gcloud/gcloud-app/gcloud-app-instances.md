---
description: gcloud app instances - view and manage your App Engine instances
---

# gcloud app instances

 To delete instance i1 of service s1 and version v1, run:

```text
  $ gcloud app instances delete i1 --service=s1 --version=v1
```

 To show all data about instance i1 for service s1 and version v1, run:

```text
  $ gcloud app instances describe --service=s1 --version=v1 i1
```

 To list all App Engine instances, run:

```text
  $ gcloud app instances list
```

To list all App Engine instances for a given service, run:

```text
  $ gcloud app instances list -s myservice
```

To list all App Engine instances for a given version, run:

```text
  $ gcloud app instances list -v v1
```

