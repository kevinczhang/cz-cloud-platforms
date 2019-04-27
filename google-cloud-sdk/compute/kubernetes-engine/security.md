# Security

## Authentication and authorization

Kubernetes supports [two types of authentication](https://kubernetes.io/docs/reference/access-authn-authz/authentication/#users-in-kubernetes):

1. **User accounts** are accounts that are known to Kubernetes, but are not managed by Kubernetes - for example, you cannot create or delete them using `kubectl`.
2. **Service accounts** are accounts that are created and managed by Kubernetes, but can only be used by Kubernetes-created entities, [such as pods](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/).

## Access control

Google Kubernetes Engine supports multiple options for managing access to resources within your project and its clusters using role-based access control \(RBAC\).

 [Kubernetes RBAC](https://cloud.google.com/kubernetes-engine/docs/concepts/access-control#rbac) is built into Kubernetes, and grants granular permissions to objects within Kubernetes clusters. Permissions exist as ClusterRole or Role objects within the cluster. RoleBinding objects grant Roles to Kubernetes users, GCP users, GCP service accounts, or [Google Groups \(beta\)](https://cloud.google.com/kubernetes-engine/docs/how-to/role-based-access-control#google-groups-for-gke).

 [Cloud IAM](https://cloud.google.com/kubernetes-engine/docs/concepts/access-control#iam) manages GCP resources, including clusters, and types of objects within clusters. Permissions are assigned to Cloud IAM _members_, which exist within GCP, G Suite, or Cloud Identity.

## Secret

 **Secrets** are secure objects which store sensitive data, such as passwords, OAuth tokens, and SSH keys, in your clusters. 

You create a Secret using the following command:

```text
kubectl create secret [TYPE] [NAME] [DATA]
```

`[TYPE]` can be one of the following:

* `generic`: Create a Secret from a local file, directory, or literal value.
* `docker-registry`: Creates a `dockercfg` Secret for use with a Docker registry. Used to authenticate against Docker registries.
* `tls`: Create a TLS secret from the given public/private key pair. The public/private key pair must exist beforehand. The public key certificate must be .PEM encoded and match the given private key.

To use a Secret with your workloads, you can specify environment variables that reference the Secret's values, or mount a volume containing the Secret.



