# Workloads on GKE

## Pod

**Pods** are the smallest, most basic deployable objects in Kubernetes. A Pod represents a single instance of a running process in your cluster.

Pods contain one or more _containers_, such as Docker containers. When a Pod runs multiple containers, the containers are managed as a single entity and share the Pod's resources. Generally, running multiple containers in a single Pod is an advanced use case.

### Pod lifecycle <a id="pod_lifecycle"></a>

Pods are ephemeral. They are not designed to run forever, and when a Pod is terminated it cannot be brought back. In general, Pods do not disappear until they are deleted by a user or by a controller.

When you run [`kubectl get pod`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get) to inspect a Pod running on your cluster, a Pod can be in one of the following possible phases:

* **Pending:** Pod has been created and accepted by the cluster, but one or more of its containers are not yet running. This phase includes time spent being scheduled on a node and downloading images.
* **Running:** Pod has been bound to a node, and all of the containers have been created. At least one container is running, is in the process of starting, or is restarting.
* **Succeeded:** All containers in the Pod have terminated successfully. Terminated Pods do not restart.
* **Failed:** All containers in the Pod have terminated, and at least one container has terminated in failure. A container "fails" if it exits with a non-zero status.
* **Unknown:** The state of the Pod cannot be determined.

## Deployment 

_Deployments_ represent a set of multiple, identical [Pods](https://cloud.google.com/kubernetes-engine/docs/concepts/pod) with no unique identities. A Deployment runs multiple replicas of your application and automatically replaces any instances that fail or become unresponsive. 

 You can [create a Deployment](https://cloud.google.com/kubernetes-engine/docs/how-to/stateless-apps#creating_a_deployment) using the [`kubectl run`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#run), [`kubectl apply`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#apply), or [`kubectl create`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#create) commands.

 To see in which order Pods are brought up and are removed, you can run [`kubectl describe deployments`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#describe).

 You can roll back an update using the [`kubectl rollout undo`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#rollout) command. You can also use `kubectl rollout pause` to temporarily halt a Deployment.

### Status and lifecycle <a id="status_and_lifecycle"></a>

Deployments can be in one of three states during its lifecycle: progressing, completed, or failed.

## StatefulSet

_StatefulSets_ represent a set of \[Pods\] with unique, persistent identities and stable hostnames that GKE maintains regardless of where they are scheduled. StatefulSets use an ordinal index for the identity and ordering of their Pods.  StatefulSets use a [Pod template](https://cloud.google.com/kubernetes-engine/docs/concepts/pod#pod_templates), which contains a [specification](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.11/#podspec-v1-core) for its Pods. 

 StatefulSets are suitable for deploying Kafka, MySQL, Redis, ZooKeeper, and other applications needing unique, persistent identities and stable hostnames. For \[stateless applications\], use [Deployments](https://cloud.google.com/kubernetes-engine/docs/concepts/deployment).

 You can [create a StatefulSet](https://cloud.google.com/kubernetes-engine/docs/how-to/stateful-apps#creating_a_statefulset) using [`kubectl apply`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#apply).

## DaemonSet

Like other workload objects, **DaemonSets** manage groups of replicated [Pods](https://cloud.google.com/kubernetes-engine/docs/concepts/pod). However, DaemonSets attempt to adhere to a one-Pod-per-node model, either across the entire cluster or a subset of nodes. As you add nodes to a [node pool](https://cloud.google.com/kubernetes-engine/docs/concepts/node-pools), DaemonSets automatically add Pods to the new nodes as needed. 

 DaemonSets are useful for deploying ongoing background tasks that you need to run on all or certain nodes, and which do not require user intervention. Examples of such tasks include storage daemons like `ceph`, log collection daemons like `fluentd`, and node monitoring daemons like `collectd`.

 You can create a DaemonSet using [`kubectl apply`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#apply) or [`kubectl create`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#create).

## ConfigMap

**ConfigMaps** bind configuration files, command-line arguments, environment variables, port numbers, and other configuration artifacts to your Pods' containers and system components at runtime. ConfigMaps allow you to separate your configurations from your Pods and components, which helps keep your workloads portable, makes their configurations easier to change and manage, and prevents hardcoding configuration data to Pod specifications.

ConfigMaps are useful for storing and sharing _non-sensitive_, unencrypted configuration information. To use sensitive information in your clusters, you must use [Secrets](https://cloud.google.com/kubernetes-engine/docs/concepts/secret).

You create a ConfigMap using the following command:

```text
kubectl create configmap [NAME] [DATA]
```

`[DATA]` can be:

* a path to a directory containing one or more configuration files, indicated using the `--from-file`flag
* key-value pairs, each specified using `--from-literal` flags

