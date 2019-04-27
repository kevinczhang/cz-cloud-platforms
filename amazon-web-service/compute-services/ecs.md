---
description: Elastic container service
---

# ECS

Elastic Container Service \(ECS\) is a Docker-compatible container service provided by AWS. It allows for easy and fast container deployment onto fleets of EC2 instances, with the added benefit of AWS highly available and fault tolerant infrastructure. ECS is great for distributed applications and microservices.

ECS is a container management service that supports Docker It allows you to easily create and manage a fleet of Docker containers on a cluster of EC2 instances

### Why use ECS/Containers? 

#### Create distributed applications and Microservices

* Create application architecture comprised of independent tasks or processes \(micro services\) 
* For example, you can have separate containers for various components of your application: Webserver Application server Message queue Backend Servers 
* This allows you to start, stop, manage, monitor, and scale each container independently

#### Batch and ETL Jobs

* Package batch and ETL jobs into containers and deploy them into a shared EC2 cluster\(s\) 
* Run different versions of the same job or multiple jobs on the same cluster 
* Share cluster capacity with other processes and/or grow jobs dynamically on-demand to improve resource utilization

#### Continuous Integration and Deployment

* By using Docker's Image versioning, you can use containers for continuous integration and deployment 
* Build processes can pull, build, and create Docker Images for your containers

### AWS Fargate 

Fargate is a way to use containers as the fundamental application building blocks while AWS manages the EC2 instances for you.

## Dockerfile:

A plain text file \(script\) that specifies all of the components that are included in the container Basically, it's the instructions for what will be placed inside a given container

## Container/Docker Image:

* A container/Docker image is built from a Dockerfile 
* The container/Docker image contains all the downloaded software, code, runtime, system tools, and libraries \(as outlined in the Dockerfile\): 
  * i.e., If the Dockerfile specifies PHP to be downloaded and installed, then the container/Docker Image will have PHP downloaded and installed.

## Container Registry:

* A container registry is a repository where container/docker images are stored and accessed from when needed 
* A container registry can be: 
  * Located on AWS via the ECR service \(Elastic Container Registry\) 
  * A 3rd party repository like Docker Hub 
  * Self-hosted registry

## ECS Task 

### ECS Task Definition:

A JSON formatted text file that contains the "blueprint" for your application, including: 

* Which container/docker image to use 
* The repository \(container registry\) the image is located in 
* Which ports should be open on the container instance 
* What data volumes should be used with the containers

### ECS Task:

* An ECS Task is the actual representation of the Task Definition on an EC2 instance inside of your container cluster 
* The ECS Agent will start/stop these tasks based on instruction/schedule

## ECS Agent:

* The ECS Agent runs on each EC2 instance in the ECS cluster.
* It communicates information about the instances to ECS, including: Running tasks and Resource Utilization.
* The ECS Agent is also responsible for starting/stopping tasks \(when told to by ECS\).

