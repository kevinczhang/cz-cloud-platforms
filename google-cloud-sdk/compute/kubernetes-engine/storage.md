# Storage

### Kubernetes storage abstractions <a id="kubernetes_storage_abstractions"></a>

Kubernetes storage abstractions provide filesystem and block-based storage to your [Pods](https://cloud.google.com/kubernetes-engine/docs/concepts/pod). They are not used with managed databases or Cloud Storage.

## Volumes

Conceptually, a volume is a directory which is accessible to all of the containers in a Pod. The volume source declared in the [Pod specification](https://cloud.google.com/kubernetes-engine/docs/concepts/pod#pod_templates) determines how the directory is created, the storage medium used, and the directory's initial contents. A Pod specifies what Volumes it contains and the path where containers mount the Volume.

Ephemeral Volume types have the same lifetimes as their enclosing Pods. These Volumes are created when the Pod is created, and they persist through container restarts. When the Pod terminates or is deleted its Volumes go with it.

### Types of volumes <a id="types_of_volumes"></a>

#### emptyDir

An ephemeral volume type that provides an empty directory that containers in the Pod can read and write from. When the Pod is removed from a node for any reason, the data in the emptyDir is deleted forever. emptyDirs are useful for scratch space and sharing data between multiple containers in a Pod.

#### [configMap](https://cloud.google.com/kubernetes-engine/docs/concepts/configmap) 

Used to make configuration data accessible to applications. The files in a configMap Volume are specified by a ConfigMap resource.

#### [secret](https://cloud.google.com/kubernetes-engine/docs/concepts/secret)

Used to make sensitive data, such as passwords, OAuth tokens, and SSH keys, available to applications.

#### [downwardAPI](https://kubernetes.io/docs/concepts/storage/volumes/#downwardapi) 

Used to make [Downward API](https://kubernetes.io/docs/tasks/inject-data-application/downward-api-volume-expose-pod-information/) data available to applications. This data includes information about the Pod and container in which an application is running in. For example, a Pod can be configured to expose a DownwardAPIVolumeFile to applications that includes the Pod's namespace and IP address.

#### [persistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)

Cluster operators can provision durable storage to be used by applications. A Pod uses a PersistentVolumeClaim to mount a Volume that is backed by this durable storage.

## Persistent Volumes

 **PersistentVolume** resources are used to manage durable storage in a cluster. On GKE, PersistentVolumes are typically backed by [Compute Engine persistent disks](https://cloud.google.com/compute/docs/disks/). PersistentVolumes can also be used with other storage types like NFS. 

Unlike [Volumes](https://cloud.google.com/kubernetes-engine/docs/concepts/volumes), the PersistentVolumes lifecycle is managed by Kubernetes. PersistentVolumes can be dynamically provisioned; the user does not have to manually create and delete the backing storage. PersistentVolumes are cluster resources that exist independently of Pods. 

 A **PersistentVolumeClaim** is a request for and claim to a PersistentVolume resource. PersistentVolumeClaim objects request a specific size, access mode, and [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/) for the PersistentVolume. If a PersistentVolume that satisfies the request exists or can be provisioned, the PersistentVolumeClaim is bound to that PersistentVolume.

