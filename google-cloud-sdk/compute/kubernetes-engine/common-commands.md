# Common Commands

## Quick start

#### To create a cluster, run the following command:

```text
gcloud container clusters create [CLUSTER_NAME]
```

where `[CLUSTER_NAME]` is the name you choose for the cluster.

#### To authenticate for the cluster, run the following command:

```text
gcloud container clusters get-credentials [CLUSTER_NAME]
```

This command configures `kubectl` to use the cluster you created.

#### To run `hello-app` in your cluster, run the following command:

```text
kubectl run hello-server --image gcr.io/google-samples/hello-app:1.0 --port 8080
```

#### To expose your application, run the following [`kubectl expose`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#expose) command:

```text
kubectl expose deployment hello-server --type LoadBalancer \
  --port 80 --target-port 8080
```

#### Inspect the `hello-server` Service by running [`kubectl get`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get):

```text
kubectl get service hello-server
```

#### Delete the application's Service by running [`kubectl delete`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#delete):

```text
kubectl delete service hello-server
```

#### Delete your cluster by running [`gcloud container clusters delete`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/delete):

```text
gcloud container clusters delete [CLUSTER_NAME]
```

## Cluster management

#### You can create, upgrade, and delete node pools individually without affecting the whole cluster:

```text
gcloud container node-pools
```

