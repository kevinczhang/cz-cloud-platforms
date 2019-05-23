---
description: >-
  GCP's unmanaged compute service is Google Compute Engine. You can think of
  Compute Engine as providing an infrastructure as a service (IaaS), because the
  system provides a robust computing infrastruct
---

# Compute Engine

## When to use Compute Engine

All workloads, OS-level control, high-performance available

* You need control over the OS.
* You need control over CPU, GPU, SSDs, RAM, etc…
* You need to lift-and-shift an existing application.
* Your workload isn't containerized.
* You are performing bulk processing and require preemptible instances

Workloads such as 3D rendering is a great example use case because it requires multiple GPUs all working together. It also benefits from Preemptive machines, allowing for lower cost processing.

However, VMs aren't just for complex computing. They're also great for running non-containerized applications. Such as content management systems, databases, build servers, etc.

## When you build on Compute Engine, you can:

* Use virtual machines \(VMs\), called [_instances_](https://cloud.google.com/compute/docs/instances), to build your application, much like you would if you had your own hardware infrastructure. You can choose from a variety of instance types to customize your configuration to meet your needs and your budget.
* Choose which global [regions and zones](https://cloud.google.com/compute/docs/zones) to deploy your resources in, giving you control over where your data is stored and used.
* Choose which operating systems, development stacks, languages, frameworks, services, and other software technologies you prefer.
* Create instances from public or private [images](https://cloud.google.com/compute/docs/images) .
* Use GCP storage technologies or any third-party technologies you prefer.
* Use [Google Cloud Launcher](https://cloud.google.com/launcher) to quickly deploy pre-configured software packages. For example, you can deploy a LAMP or MEAN stack with just a few clicks.
* Create [instance groups](https://cloud.google.com/compute/docs/instance-groups) to more easily manage multiple instances together.
* Use [autoscaling with an instance group](https://cloud.google.com/compute/docs/autoscaler) to automatically add and remove capacity.
* Attach and detach [disks](https://cloud.google.com/compute/docs/disks) as needed.
* [Use SSH to connect](https://cloud.google.com/compute/docs/instances/connecting-to-instance) directly to your instances. \(gcloud compute ssh or add public key as metadata then use ssh\)

## Steps to create compute engine

1. gcloud projects create
2. gcloud billing accounts list
3. gcloud projects billing account link projectID --billing-account=...
4. create VPC and subnets
5. Create VM instance
6. Create firewall rules

As cloud engineers, we know how important backups are to a company. Disk snapshots allow us to create an incremental backup of our persistent disks.

Images are copies of an instance, and they're robust enough to serve as both a backup and as a "golden image" that contains all of our code and configuration.

