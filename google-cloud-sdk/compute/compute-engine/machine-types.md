# Machine Types

A machine type specifies a particular collection of virtualized hardware resources available to a virtual machine \(VM\) instance, including the system memory size, virtual CPU \(vCPU\) count, and maximum persistent disk capability.

## Predefined machine types

Standard machine types: Standard machine types are suitable for tasks that have a balance of CPU and memory needs. Standard machine types have 3.75 GB of memory per vCPU.

High-memory machine types: High-memory machine types are ideal for tasks that require more memory relative to vCPUs. High-memory machine types have 6.50GB of system memory per vCPU.

High-CPU machine types: High-CPU machine types are ideal for tasks that require more vCPUs relative to memory. High-CPU machine types have 0.90 GB of memory per vCPU.

Shared-core machine types:

| f1-micro | Micro machine type with 0.2 vCPU, 0.60 GB of memory, backed by a shared physical core |
| :--- | :--- |
| g1-small | Shared-core machine type with 0.5 vCPU, 1.70 GB of memory, backed by a shared physical core. |

Memory-optimized machine types: Memory-optimized machine types are ideal for tasks that require intensive use of memory with higher memory to vCPU ratios than high-memory machine types. 

Custom machine types

If none of the predefined machine types match your needs, you can independently specify the number of vCPUs and the amount of memory for your instance.

GPUs and machine types

You can attach GPUs only to instances with a [predefined machine type](https://cloud.google.com/compute/docs/machine-types#predefined_machine_types) or [custom machine type](https://cloud.google.com/compute/docs/machine-types#custom_machine_types) that you are able to create in a zone. GPUs are not supported on [shared-core machine types](https://cloud.google.com/compute/docs/machine-types#sharedcore) or [memory-optimized machine types](https://cloud.google.com/compute/docs/machine-types#megamem).

Instances with lower numbers of GPUs are limited to a maximum number of vCPUs. 

