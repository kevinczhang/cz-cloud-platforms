---
description: 'gcloud services - list, enable and disable APIs and services'
---

# gcloud services

To disable a service called `my-consumed-service` for the active project, run:

```text
  $ gcloud services disable my-consumed-service
```

To run the same command asynchronously \(non-blocking\), run:

```text
  $ gcloud services disable my-consumed-service --async
```

To enable a service called `my-consumed-service` on the current project, run:

```text
  $ gcloud services enable my-consumed-service
```

To run the same command asynchronously \(non-blocking\), run:

```text
  $ gcloud services enable my-consumed-service --async
```

To enable services called `service1`, `service2`, and `service3` on the current project, run:

```text
  $ gcloud services enable service1 service2 service3
```

To list the services the current project has enabled for consumption, run:

```text
  $ gcloud services list --enabled
```

To list the services the current project can enable for consumption, run:

```text
  $ gcloud services list --available
```

