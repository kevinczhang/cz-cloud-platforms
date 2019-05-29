# VPC sharing and peering

#### Shared VPC <a id="shared_vpc"></a>

You can share a VPC network from one project \(called a host project\) to other projects in your GCP organization. 

A **Shared VPC network** is a [VPC network](https://cloud.google.com/vpc/docs/vpc) defined in a host project and made available as a centrally shared network for[eligible resources](https://cloud.google.com/vpc/docs/shared-vpc#resources_that_can_be_attached_to_shared_vpc_networks_from_a_service_project) in service projects. Shared VPC networks can be either [auto or custom mode](https://cloud.google.com/vpc/docs/vpc#subnet-ranges), but [legacy networks](https://cloud.google.com/compute/docs/vpc/legacy) are not supported.

A project that participates in Shared VPC is either a _host project_ or a _service project_:

* A **host project** contains one or more [Shared VPC networks](https://cloud.google.com/vpc/docs/shared-vpc#shared_vpc_networks). A [Shared VPC Admin](https://cloud.google.com/vpc/docs/shared-vpc#iam_in_shared_vpc) must first [enable](https://cloud.google.com/vpc/docs/provisioning-shared-vpc#enable-shared-vpc-host) a project as a host project. After that, a Shared VPC Admin can attach one or more _service projects_ to it.
* A **service project** is any project that has been [attached](https://cloud.google.com/vpc/docs/provisioning-shared-vpc#create-shared) to a host project by a Shared VPC Admin. This attachment allows it to participate in Shared VPC. It's a common practice to have multiple service projects operated and administered by different departments or teams in your organization.
* A project cannot be both a host and a service project simultaneously. Thus, a service project cannot be a host project to further service projects.
* You can create and use multiple host projects; however, each service project can only be attached to a single host project. See the [Multiple host projects example](https://cloud.google.com/vpc/docs/shared-vpc#example_multiple_host_projects) for an illustration.

#### VPC Network Peering <a id="vpc_network_peering"></a>

VPC Network Peering allows you to build SaaS \([Software-as-a-Service](https://wikipedia.org/wiki/Software_as_a_service)\) ecosystems in GCP, making services available privately across different VPC networks, whether the networks are in the same project, different projects, or projects in different organizations.

