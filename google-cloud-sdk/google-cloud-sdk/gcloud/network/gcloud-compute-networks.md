---
description: 'List, create, and delete Google Compute Engine networks.'
---

# gcloud compute networks

`gcloud compute networks` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/#GCLOUD-WIDE-FLAGS) `…`\]

`GROUP` is one of the following:

* [`peerings`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings)List, create, and delete Google Compute Engine network peerings.
* [`subnets`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets)List, describe, and delete Google Compute Engine subnetworks.

`COMMAND` is one of the following:

* [`create`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/create)Create a Google Compute Engine network.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/delete)Delete Google Compute Engine networks.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/describe)Describe a Google Compute Engine network.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/list)List Google Compute Engine networks.
* [`update`](https://cloud.google.com/sdk/gcloud/reference/compute/networks/update)Update a Google Compute Engine network.

## Creating an auto mode network

[Auto mode](https://cloud.google.com/vpc/docs/vpc#subnet-ranges) networks create one [subnet](https://cloud.google.com/vpc/docs/vpc#vpc_networks_and_subnets) in each GCP region automatically when you create the network. As new regions become available, new subnets in those regions are automatically added to the auto mode network. IP ranges for the automatically created subnets come from a [predetermined set of ranges](https://cloud.google.com/vpc/docs/vpc#ip-ranges). All auto mode networks use the same set of IP ranges.

Create an auto mode network using the following `gcloud` command:

```text

gcloud compute networks create NETWORK_NAME \
    --subnet-mode=auto \
    --bgp-routing-mode=DYNAMIC_ROUTING_MODE
```

Replace the placeholders with valid values:

* NETWORK\_NAME is a name for the VPC network.
* DYNAMIC\_ROUTING\_MODE can be either `global` or `regional` to control the behavior of Cloud Routers in the network. For more information, refer to [dynamic routing mode](https://cloud.google.com/vpc/docs/vpc#routing_for_hybrid_networks).

## Creating a new VPC network with custom subnets

For custom mode VPC networks, create a network, then create the subnets that you want within a region. You do not have to specify subnets for all regions right away, or even at all, but you cannot create instances in a region that has no subnet defined.

Create a new custom mode network using the following `gcloud` command. After you have created your network, add subnets to it by following the [adding subnets](https://cloud.google.com/vpc/docs/using-vpc#add-subnets) directions.

```text
gcloud compute networks create NETWORK_NAME \
    --subnet-mode=custom \
    --bgp-routing-mode=DYNAMIC_ROUTING_MODE
```

Replace the placeholders with valid values:

* NETWORK\_NAME is a name for the VPC network.
* DYNAMIC\_ROUTING\_MODE can be either `global` or `regional` to control the route advertisement behavior of Cloud Routers in the network. For more information, refer to [dynamic routing mode](https://cloud.google.com/vpc/docs/vpc#routing_for_hybrid_networks).

### Viewing networks <a id="viewing-networks"></a>

1. List the networks in your project, as shown in the following example.

   ```text
   gcloud compute networks list
   ```

   The command lists all of your VPC and legacy networks. Legacy networks show a subnet creation mode of `LEGACY`, while VPC networks show either `AUTO` or `CUSTOM`.

   ```text
   NAME             SUBNET_MODE  BGP_ROUTING_MODE  IPV4_RANGE     GATEWAY_IPV4
   custom-network   CUSTOM       REGIONAL
   default          AUTO         REGIONAL
   legacy-network1  LEGACY       REGIONAL          10.240.0.0/16  10.240.0.1
   ```

2. Describe a network to view its details, such as its peering connections and subnets.

   ```text
   gcloud compute networks describe NETWORK_NAME
   ```

## Working with subnets

#### Listing subnets <a id="listing_existing_subnets"></a>

* Use this command to list all subnets in all VPC networks, in all regions:

  ```text
  gcloud compute networks subnets list
  ```

* Use this command to list all subnets in a particular VPC network, replacing NETWORK with the name of the network:

  ```text
  gcloud compute networks subnets list \
     --network=NETWORK
  ```

* Use this command to list all subnets in a particular region, replacing REGION with a region name:

  ```text
  gcloud compute networks subnets list \
     --region=REGION
  ```

#### Describing a subnet <a id="describing_an_existing_subnet"></a>

Describe the subnet using the following `gcloud` command, replacing SUBNET\_NAME with its name and REGION with its region.

```text
gcloud compute networks subnets describe SUBNET_NAME \
--region=REGION
```

#### Adding subnets <a id="add-subnets"></a>

The following `gcloud` command creates a new subnet in a given network.

```text
gcloud compute networks subnets create SUBNET_NAME \
    --network=NETWORK \
    --range=PRIMARY_RANGE \
    --region=REGION
```

Replace the placeholders with valid values:

* SUBNET\_NAME is a name for the new subnet.
* NETWORK is the name of the VPC network that will contain the new subnet.
* PRIMARY\_RANGE is the primary IP range for the new subnet, in CIDR notation.
* REGION is the GCP region in which the new subnet will be created.

You can modify the previous command with the following optional flags:

* `--secondary-range=`SECONDARY\_RANGE: Replace SECONDARY\_RANGE with a secondary range in CIDR notation. You can add up to five secondary ranges.
* `--enable-flow-logs`: Enables [VPC Flow Logs](https://cloud.google.com/vpc/docs/using-flow-logs) in the subnet at creation time.
* `--enable-private-ip-google-access`: Enables [Private Google Access](https://cloud.google.com/vpc/docs/private-access-options) in the subnet at creation time.

#### Deleting subnets <a id="deleting_subnets"></a>

Use the following `gcloud` command to delete a subnet:

```text
gcloud compute networks subnets delete SUBNET_NAME \
    --region=REGION
```

Replace the placeholders with valid values:

* SUBNET\_NAME is the name of the subnet to delete.
* REGION is the region where the subnet exists.

#### Expanding a primary IP range <a id="expand-subnet"></a>

Expand the primary IP range of a subnet with the following `gcloud` command:

```text
gcloud compute networks subnets expand-ip-range SUBNET_NAME \
  --region=REGION \
  --prefix-length=PREFIX_LENGTH
```

Replace the placeholders with valid values:

* SUBNET\_NAME is the name of the subnet.
* REGION is the region in which the subnet is located.
* PREFIX\_LENGTH is a subnet mask size in bits. If the primary IP range is `10.1.2.0/24`, you can supply `20` to reduce the subnet mask to 20 bits, which changes the primary IP range to `10.1.2.0/20`.

#### Editing secondary ranges <a id="edit-secondary"></a>

Add a new secondary IP range to a subnet using the following `gcloud` command:

```text
gcloud compute networks subnets update SUBNET_NAME \
  --region=REGION \
  --add-secondary-ranges=SECONDARY_RANGE_NAME=SECONDARY_RANGE
```

Replace the placeholders with valid values:

* SUBNET\_NAME is the name of the subnet.
* REGION is the region in which the subnet is located.
* SECONDARY\_RANGE\_NAME is a name for the secondary range.
* SECONDARY\_RANGE is the secondary IP range in CIDR notation.

Remove a secondary IP range from a subnet using the following `gcloud` command:

```text
gcloud compute networks subnets update SUBNET_NAME \
  --region=REGION \
  --remove-secondary-ranges=SECONDARY_RANGE_NAME
```

Replace the placeholders with valid values:

* SUBNET\_NAME is the name of the subnet.
* REGION is the region in which the subnet is located.
* SECONDARY\_RANGE\_NAME is the name of the secondary range to be removed.

## Converting to custom mode

Convert an auto mode network to a custom mode network using the following command, replacing NETWORK\_NAME with the network's name.

```text
gcloud compute networks update NETWORK_NAME \
    --switch-to-custom-subnet-mode
```

## Deleting a network

Delete a network by using the following `gcloud` command, replacing NETWORK\_NAME with the name of the network to remove.

```text
gcloud compute networks delete NETWORK_NAME
```

## Monitoring your VPC network

You can enable logging of network flows to and from VMs. See [Using VPC Flow Logs](https://cloud.google.com/vpc/docs/using-flow-logs) for instructions.

You can enable logging for firewall rules to see which rules allowed or blocked which traffic. See [Using Firewall Rules Logging](https://cloud.google.com/vpc/docs/using-firewall-rules-logging) for instructions.

## Reserving a new static external IP address

To reserve a new static external IP address using `gcloud compute`, use the [`addresses create`](https://cloud.google.com/sdk/gcloud/reference/compute/addresses/create) sub-command and specify whether you want to reserve a global or regional IP address:

```text
gcloud compute addresses create [ADDRESS_NAME] \
    [--region [REGION] | --global ] \
    [--ip-version [IPV4 | IPV6]]
```

where:

* `[ADDRESS_NAME]` is the name you want to call this address.
* If you are specifying a regional IP address, provide the desired `[REGION]` for the request. This should be the same region as the resource you want to attach the IP address to.
* If it is a global IP address, specify the `--global` flag. If you want an IPv6 address, specify both `--global` and `--ip-version IPV6` flags. `IPv6` addresses can only be global and can only be used with global HTTP\(S\), SSL proxy, and TCP proxy load balancers.

To assign a static external IP address, use the `--address` flag during instance creation and provide the static external IP address:

```text
gcloud compute instances create [INSTANCE_NAME] --address [IP_ADDRESS]
```

where:

* `[INSTANCE_NAME]` is the name of the instance.
* `[IP_ADDRESS]` is the IP address to assign to the instance. Use the IP address, not the address name.

## Reserving a new static internal IP address

Using the `gcloud` tool, run the `compute addresses create` command:

```text
gcloud compute addresses create [ADDRESS_NAME] [[ADDRESS_NAME]..] \
    --region [REGION] --subnet [SUBNETWORK] \
    --addresses [IP_ADDRESS]
```

where:

* `[ADDRESS_NAME]` is desired names of one or more addresses to create.
* `[REGION]` is the region for this request.
* `[SUBNETWORK]` is the subnet for this internal IP address.
* `[IP_ADDRESS]` is the IP address to reserve, which must be within the subnet's IP range. If unspecified, one will be automatically allocated from the subnet.

For example, to reserve an automatically allocated internal IP address from a subnet:

```text
gcloud compute addresses create example-address-1 \
    --region us-central1 --subnet subnet-1
```

To reserve a specific internal IP address from a subnet:

```text
gcloud compute addresses create example-address-1 \
    --region us-central1 --subnet subnet-1 --addresses 10.128.0.12
```

You can create multiple addresses by passing in more than one address name. However, all the addresses will be reserved in the same subnet. For example:

```text
gcloud compute addresses create example-address-1 example-address-2 \
    --region us-central1 --subnet subnet-1 \
    --addresses 10.128.0.12,10.128.0.13
```

## Locating the external and internal IP address for an instance

To view the internal and external IP addresses for your instance using `gcloud compute`, use the [`instances list`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/list) sub-command.

```text
gcloud compute instances list
```

Your output should resemble the following:

```text
NAME              ZONE            MACHINE_TYPE     PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP    STATUS
hulk              us-central1-c   n1-ultramem-160  true         192.0.2.1                   RUNNING
my-instance       us-central1-c   n1-standard-1                 192.51.100.1  203.224.0.113 RUNNING
```

To view the internal or external IP address for a specific instance using `gcloud compute`, use the [`instances describe`](https://cloud.google.com/sdk/gcloud/reference/compute/instances/describe) sub-command with a `--format` flag to filter the output. For example:

* To view the internal IP for a specific instance, run the following command:

  ```text
  gcloud compute instances describe [INSTANCE_NAME] --format='get(networkInterfaces[0].networkIP)'

  192.51.100.1
  ```

* To view the external IP for a specific instance, run the following command:

  ```text

  gcloud compute instances describe [INSTANCE_NAME] --format='get(networkInterfaces[0].accessConfigs[0].natIP)'
  203.224.0.113
  ```

where `[INSTANCE_NAME]` is the name of the instance whose internal or external IP you want to view.

