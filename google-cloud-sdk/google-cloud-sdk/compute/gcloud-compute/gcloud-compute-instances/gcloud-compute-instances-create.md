# gcloud compute instances create

 `gcloud compute instances create` facilitates the creation of Google Compute Engine virtual machines. For example, running:

```text
  $ gcloud compute instances create example-instance-1 \
      example-instance-2 example-instance-3 --zone us-central1-a
```

will create three instances called `example-instance-1`, `example-instance-2`, and `example-instance-3` in the`us-central1-a` zone.

When an instance is in RUNNING state and the system begins to boot, the instance creation is considered finished, and the command returns with a list of new virtual machines. Note that you usually cannot log into a new instance until it finishes booting. Check the progress of an instance using [`gcloud compute instances get-serial-port-output`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/get-serial-port-output).

 `gcloud compute instances create` [`INSTANCE_NAMES`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create#INSTANCE_NAMES) \[[`INSTANCE_NAMES`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create#INSTANCE_NAMES) …\]

## FLAGS

* `--boot-disk-auto-delete:` Automatically delete boot disks when their instances are deleted. Enabled by default, use `--no-boot-disk-auto-delete` to disable.
* `--boot-disk-device-name`=`BOOT_DISK_DEVICE_NAME:`The name the guest operating system will see for the boot disk. This option can only be specified if a new boot disk is being created \(as opposed to mounting an existing persistent disk\).
* `--boot-disk-type`=`BOOT_DISK_TYPE:`The type of the boot disk. This option can only be specified if a new boot disk is being created \(as opposed to mounting an existing persistent disk\). To get a list of available disk types, run `$` [`gcloud compute disk-types list`](https://cloud.google.com/sdk/gcloud/reference/compute/disk-types/list).
* `--create-disk`=\[`PROPERTY`=`VALUE`,…\]: Creates and attaches persistent disks to the instances.
* `--deletion-protection:`Enables deletion protection for the instance.
* `--disk`=\[`auto-delete`=`AUTO-DELETE`\],\[`boot`=`BOOT`\],\[`device-name`=`DEVICE-NAME`\],\[`mode`=`MODE`\],\[`name`=`NAME`\]: Attaches persistent disks to the instances. The disks specified must already exist.
* `--machine-type`=`MACHINE_TYPE`Specifies the machine type used for the instances. To get a list of available machine types, run 'gcloud compute machine-types list'. If unspecified, the default type is n1-standard-1.
* `--maintenance-policy`=`MAINTENANCE_POLICY`Specifies the behavior of the instances when their host machines undergo maintenance. The default is MIGRATE. `MAINTENANCE_POLICY` must be one of: MIGRATE or TERMINATE
* `--metadata`=`KEY`=`VALUE`,\[`KEY`=`VALUE`,…\]: Metadata to be made available to the guest operating system running on the instances. Each metadata entry is a key/value pair separated by an equals sign. The following metadata keys have special meanings:
  * `startup-script:`Specifies a script that will be executed by the instances once they start running. For convenience, `--metadata-from-file` can be used to pull the value from a file.
  * `startup-script-url`Same as `startup-script` except that the script contents are pulled from a publicly-accessible location on the web.
* `--network`=`NETWORK:`Specifies the network that the instances will be part of. If --subnet is also specified subnet must be a subnetwork of network specified by --network. If neither is specified, this defaults to the "default" network.
* `--preemptible:`If provided, instances will be preemptible and time-limited. Instances may be preempted to free up resources for standard VM instances, and will only be able to run for a limited amount of time. Preemptible instances can not be restarted and will not migrate.
* `--restart-on-failure:`The instances will be restarted if they are terminated by Compute Engine. This does not affect terminations performed by the user. Enabled by default, use `--no-restart-on-failure` to disable.
* `--source-instance-template`=`SOURCE_INSTANCE_TEMPLATE`The name of the instance template that the instance will be created from.

  Users can also override machine type and labels. Values of other flags will be ignored and `--source-instance-template` will be used instead.

* `--subnet`=`SUBNET`Specifies the subnet that the instances will be part of. If --network is also specified subnet must be a subnetwork of network specified by --network.
* `--tags`=`TAG`,\[`TAG`,…\]: Specifies a list of tags to apply to the instance. These tags allow network firewall rules and routes to be applied to specified VM instances. See [`gcloud compute firewall-rules create`](https://cloud.google.com/sdk/gcloud/reference/compute/firewall-rules/create)\(1\) for more details.
* `--zone`=`ZONE`Zone of the instances to create. If not specified and the `compute/zone` property isn't set, you may be prompted to select a zone.
* Custom machine type extensions.
  * `--custom-cpu`=`CUSTOM_CPU`A whole number value indicating how many cores are desired in the custom machine type. This flag must be specified if any of the other arguments in this group are specified.
  * `--custom-memory`=`CUSTOM_MEMORY`A whole number value indicating how much memory is desired in the custom machine type. A size unit should be provided \(eg. 3072MB or 9GB\) - if no units are specified, GB is assumed. This flag must be specified if any of the other arguments in this group are specified.
  * `--custom-extensions`Use the extended custom machine type.
* At most one of these may be specified:
  * `--image`=`IMAGE`Specifies the boot image for the instances. For each instance, a new boot disk will be created from the given image. Each boot disk will have the same name as the instance. To view a list of public images and projects, run `$` [`gcloud compute images list`](https://cloud.google.com/sdk/gcloud/reference/compute/images/list). It is best practice to use `--image` when a specific version of an image is needed.

    When using this option, `--boot-disk-device-name` and `--boot-disk-size` can be used to override the boot disk's device name and size, respectively.

  * `--image-family`=`IMAGE_FAMILY`The family of the image that the boot disk will be initialized with. When a family is specified instead of an image, the latest non-deprecated image associated with that family is used. It is best practice to use `--image-family` when the latest version of an image is needed.
* At most one of these may be specified:
  * `--service-account`=`SERVICE_ACCOUNT`A service account is an identity attached to the instance. Its access tokens can be accessed through the instance metadata server and are used to authenticate applications on the instance. The account can be set using an email address corresponding to the required service account. You can explicitly specify the Compute Engine default service account using the 'default' alias.

    If not provided, the instance will get project's default service account.



