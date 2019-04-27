# Common commands

## instances

 To create an instance with the name `my-redis-instance`, run:

```text
  $ gcloud beta redis instances create my-redis-instance
```

To delete an instance with the name `my-redis-instance`, run:

```text
  $ gcloud beta redis instances delete my-redis-instance
```

To display the details for an instance with the name `my-redis-instance`, run:

```text
  $ gcloud beta redis instances describe my-redis-instance
```

To list all the instances, run:

```text
  $ gcloud beta redis instances list
```

To set the label `env` to `prod` for an instance with the name `my-redis-instance`, run:

```text
  $ gcloud beta redis instances my-redis-instance \
      --update-labels=env=prod
```



