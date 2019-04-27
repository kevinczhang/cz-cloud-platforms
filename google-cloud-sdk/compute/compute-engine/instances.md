---
description: An instance is an individual VM.
---

# VM Instances

Compute Engine is all about virtual machines\(VMs\). It's optimal for workloads where you need to have control of the OS; where you need ultra-high performance\(GPUs and local SSDs\); or where container orchestration isn't required. To create a new VM instance, we need to choose 

1. **Region**, **Zone**, **Machine type** \(CPU, GPU and memory\)
2. I**mages** \(Container image or Boot disk \(OS images, Application images, Custom images, Snapshots, or Existing disks\)\), 
3. **Identity and API access rules** \(service account and access scopes \(Allow default access, Allow full access to all Cloud APIs, or Set access for each API\)\).
4. **Firewall** \(Allow HTTP traffic or Allow HTTPS traffic\).

## Management

#### Deletion protection

By setting the `deletionProtection` flag, a VM instance can be protected from accidental deletion. Only a user that has been granted a role with `compute.instances.create` permission can reset the flag to allow the resource to be deleted.

#### Startup script

Create and run your own startup scripts on your virtual machines to perform automated tasks every time your instance boots up. A startup script is specified through the [metadata server](https://cloud.google.com/compute/docs/metadata), using startup script metadata keys. You can use the `gcloud` command-line tool, the API, or the [Google Cloud Platform Console](https://console.cloud.google.com/) to provide a startup script.

#### Metadata

Every instance stores its metadata on a metadata server. You can query this metadata server programmatically, from within the instance and from the Compute Engine API, for information about the instance, such as the instance's host name, instance ID, startup and shutdown scripts, custom metadata, and service account information. Your instance automatically has access to the metadata server API without any additional authorization.

Metadata is stored in the format `key:value`. There is a default set of metadata entries that every instance has access to. To access the metadata server, query the `http://metadata.google.internal/computeMetadata/v1/`URL.

#### Preemptibility

A preemptible VM is an instance that you can create and run at a much [lower price](https://cloud.google.com/compute/pricing#machinetype) than normal instances. Great for batch processing jobs can run on preemptible instances. 

* Compute Engine might terminate preemptible instances at any time due to system events. 
* Compute Engine always terminates preemptible instances after they run for 24 hours. 
* Preemptible instances cannot [live migrate](https://cloud.google.com/compute/docs/instances/live-migration#preemptiblemaintenance) to a regular VM instance, or be set to automatically restart when there is a maintenance event.

Compute Engine performs the following steps to preempt an instance:

1. Compute Engine sends a preemption notice to the instance in the form of an [ACPI G2 Soft Off](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Power_states)signal. You can use a [shutdown script](https://cloud.google.com/compute/docs/instances/create-start-preemptible-instance#handle_preemption) to handle the preemption notice and complete cleanup actions before the instance stops.
2. If the instance does not stop after 30 seconds, Compute Engine sends an [ACPI G3 Mechanical Off](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Power_states) signal to the operating system.
3. Compute Engine transitions the instance to a `TERMINATED` state.

#### On host maintenance 

When Compute Engine performs periodic infrastructure maintenance, it can migrate your VM instances to other hardware without downtime or Terminate VM instance.

#### Automatic restart 

Compute Engine can automatically restart VM instances if they are terminated for non-user-initiated reasons \(maintenance event, hardware failure, software failure and so on\)

## Security

Shielded VM offers verifiable integrity of your Compute Engine VM instances, so you can be confident your instances haven't been compromised by boot- or kernel-level [malware](https://en.wikipedia.org/wiki/Malware) or [rootkits](https://en.wikipedia.org/wiki/Rootkit). Shielded VM's verifiable integrity is achieved through the use of [Secure Boot](https://cloud.google.com/security/shielded-cloud/shielded-vm#secure-boot), [virtual trusted platform module \(vTPM\)](https://cloud.google.com/security/shielded-cloud/shielded-vm#vtpm)-enabled [Measured Boot](https://cloud.google.com/security/shielded-cloud/shielded-vm#measured-boot), and [integrity monitoring](https://cloud.google.com/security/shielded-cloud/shielded-vm#integrity-monitoring).

Secure Boot helps ensure that the system only runs authentic software by verifying the digital signature of all boot components, and halting the boot process if signature verification fails.

A vTPM is a virtualized [trusted platform module](https://trustedcomputinggroup.org/trusted-platform-module-tpm-summary/), which is a specialized computer chip you can use to protect objects, like keys and certificates, that you use to authenticate access to your system. 

During Measured Boot, a hash of each component \(for example, the firmware, bootloader, or kernel\) is created as the component is loaded, and that hash is then concatenated and rehashed with the hashes of any components that have already been loaded.

Integrity monitoring helps you understand and make decisions about the state of your VM instances.

#### SSH Keys

These keys allow access only to this instance, unlike [project-wide SSH keys](https://console.cloud.google.com/compute/metadata/sshKeys?project=agile-entry-237502&folder&organizationId). We can also block all project-wide SSH keys.

## Disks

We can select if you want to delete boot disk when instance is deleted.

#### Encryption 

* Google-managed key \(No configuration required\)
* Customer-managed key \(Manage via Google Cloud Key Management Service\).
* Customer-supplied key \(Manage outside Google Cloud\)

#### Additional disks \(Add new disk or Attach existing disk.\)

Every Compute Engine VM instance is attached to at least one disk as a boot disk and for persistent storage. A persistent disk can be a standard \(HDD\) or a solid-state \(SSD\) drive. You can also attach an ephemeral local SSD for high-performance I/O.

#### Parameters needed for creating a disk

1. Type: Standard persistent disk or SSD persistent disk.
2. Replicate this disk within region. \(max two zones\)
3. Snapshot schedule \(Use snapshot schedules to automate disk backups. \)
4. Source type \(Blank disk or Snapshot\)
5. Encryption \(same as above\)
6. Physical block size \(KB\) \(4 or 16 which can't be changed later\)

## Networking

* Network tags \(Assign network tags to apply firewall rules to specific VM instances.\)
* Hostname \(Set a custom hostname for this instance or leave it default\)
* Network interfaces \(Network, Subnetwork, Primary internal IP, External IP, IP forwarding, Public DNS PTR Record\)

## Sole-tenant nodes

A sole-tenant node is a physical Compute Engine server that is dedicated to hosting VM instances only for your specific project. Use sole-tenant nodes to keep your instances physically separated from instances in other projects, or to group your instances together on the same host hardware.

## Overview

Connecting into Linux use SSH with port 22 while windows using RDP. Compute Engine instances can run the [public images](https://cloud.google.com/compute/docs/images) for Linux and Windows Server that Google provides as well as private custom images that you can [create](https://cloud.google.com/compute/docs/images/create-delete-deprecate-private-images) or [import from your existing systems](https://cloud.google.com/compute/docs/images/importing-virtual-disks). You can also [deploy Docker containers](https://cloud.google.com/compute/docs/containers/deploying-containers), which are automatically launched on instances running the [Container-Optimized OS](https://cloud.google.com/container-optimized-os/docs/) public image.

An instance can have the following states:

* PROVISIONING - Resources are being allocated for the instance. The instance is not running yet.
* STAGING - Resources have been acquired and the instance is being prepared for first boot.
* RUNNING - The instance is booting up or running. You can connect to the instance shortly after it enters this state.
* STOPPING - The instance is being stopped. This can be because a user has made a request to [stop the instance](https://cloud.google.com/compute/docs/instances/stop-start-instance) or there was a failure. This is a temporary status and the instance will move to TERMINATED once the instance has stopped.
* TERMINATED - A user stopped the instance, or the instance encountered a failure. [Start](https://cloud.google.com/compute/docs/instances/stop-start-instance#starting_a_stopped_instance) the instance again or [delete](https://cloud.google.com/compute/docs/instances/deleting-instance) it.

