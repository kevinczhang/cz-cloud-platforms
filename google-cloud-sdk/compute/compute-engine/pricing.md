---
description: Google Compute Engine charges for usage based on the following price sheet.
---

# Pricing

 Disk size, machine type memory, and network usage are calculated in gigabytes \(GB\), where 1 GB is 230 bytes. This unit of measurement is also known as a [gibibyte \(GiB\)](https://wikipedia.org/wiki/Gibibyte).

### Billing model <a id="billingmodel"></a>

The following billing model applies to all vCPUs, GPUs, and memory resources. 

1. All vCPUs, GPUs, and GB of memory are charged a minimum of **1 minute**. For example, if you run your virtual machine for 30 seconds, you will be billed for 1 minute of usage.
2. After 1 minute, instances are charged in **1 second increments**.

### Resource-based pricing <a id="pricing"></a>

Compute Engine machine resources can be broken down into the following categories:

* [Predefined vCPUs and memory](https://cloud.google.com/compute/pricing#predefined), which are used in `n1-standard`, `n1-highcpu`, and `n1-highmem` machine types as well as [sole-tenant nodes](https://cloud.google.com/compute/pricing#nodes).
* [Custom vCPUs and memory](https://cloud.google.com/compute/pricing#custommachinetypepricing), which are used in custom machine types that allow you to select a specific number of vCPUs and memory.
* [Memory-optimized vCPUs and memory](https://cloud.google.com/compute/pricing#memory-optimized), which are used in `n1-megamem` and `n1-ultramem` machine types that have preset number of vCPUs and a high ratio of memory for each vCPU.
* [Shared-core machine types](https://cloud.google.com/compute/pricing#sharedcore), which use partial vCPUs and are cost-effective for running small, non-resource intensive applications. Shared-core machine types are still billed as a single unit rather than as separate vCPU and memory resources.

Your vCPU and memory usage for each of these categories can receive one of the following discounts:

* [Sustained use discounts](https://cloud.google.com/compute/docs/sustained-use-discounts)
* [Committed use discounts](https://cloud.google.com/compute/docs/instances/signing-up-committed-use-discounts)
* [Discounts for preemptible VM instances](https://cloud.google.com/compute/docs/instances/preemptible)

Discount types cannot be combined. Preemptible VM instances cannot receive sustained use discounts or committed use discounts.

