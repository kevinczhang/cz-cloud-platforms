# gcloud compute ssh

 `gcloud compute ssh` is a thin wrapper around the `ssh(1)` command that takes care of authentication and the translation of the instance name into an IP address.

Note, this command does not work when connecting to Windows VMs. To connect to a Windows instance using a command-line method, refer to this guide: [https://cloud.google.com/compute/docs/instances/connecting-to-instance\#windows\_cli](https://cloud.google.com/compute/docs/instances/connecting-to-instance#windows_cli)

The default network comes preconfigured to allow ssh access to all VMs. If the default network was edited, or if not using the default network, you may need to explicitly enable ssh access by adding a firewall-rule:

```text
  $ gcloud compute firewall-rules create --network=NETWORK           \
        default-allow-ssh --allow tcp:22
```

gcloud compute ssh ensures that the user's public SSH key is present in the project's metadata. If the user does not have a public SSH key, one is generated using `ssh-keygen(1)` \(if the `--quiet` flag is given, the generated key will have an empty passphrase\).

## Examples

 To SSH into 'example-instance' in zone `us-central1-a`, run:

```text
  $ gcloud compute ssh example-instance --zone us-central1-a
```

You can also run a command on the virtual machine. For example, to get a snapshot of the guest's process tree, run:

```text
  $ gcloud compute ssh example-instance --zone us-central1-a \
      --command "ps -ejH"
```

If you are using the Google Container-Optimized virtual machine image, you can SSH into one of your containers with:

```text
  $ gcloud compute ssh example-instance --zone us-central1-a \
      --container CONTAINER
```

