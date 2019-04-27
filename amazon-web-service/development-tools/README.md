# Development Tools

AWS offers a variety of developer tools used for tasks ranging from source control to deployment to advanced application debugging.

## X-Ray

AWS X-Ray traces requests as they move through your applications. It collects data and makes it available to view, filter, and sort. You can then use the data to gain insights and identify potential optimizations to make inside your application.

### X-Ray Concepts

* **Segments** - Data about the work done by your application \(can include data on: the request, the response, subsegments, and issues\) 
* **Subsegments** - A more granular view of data inside of segments 
* **Service Graph** - A JSON document that contains information about how your application's services and resources interact \(this can create a visualized service map\) 
* **Traces** - Trace IDs track requests as they go through your applications: 
  * The first X-Ray supported service to interact with a request adds an HTTP trace ID header 
  * The trace ID header propagates downstream to track the request as it moves through the system 
* **Sampling** - X-Ray applies an algorithm to sample request data but you can configure the frequency of sampling \(e.g. to reduce it on high-volume or lower-volume requests\) 
* **Tracing Header** - Examples: 
  * X-Amzn-Trace-Id: Root=1-5759e988-bd862e3fe1be46a994272793;Sampled=1 
  * X-Amzn-Trace-Id: Root=1-5759e988-bd862e3fe1be46a994272793;Parent=53995c3f42cd8ad8;Sampled=1 
* **Filter Expressions** - Used in the X-Ray console to search through your traces by different characteristics \(e.g. specific trace ids, partial URL paths, annotations\) 
* **Annotations and Metadata** - additional way to store searchable \(annotations\) and non-searchable \(metadata\) data about traces 
* **Errors, Faults, and Exceptions** - X-Ray tracks application errors and categorizes them as: 
  * Error – Client errors \(400 series errors\) 
  * Fault – Server faults \(500 series errors\) 
  * Throttle – Throttling errors \(429 Too Many Requests\)

## CodeCommit

AWS CodeCommit is a managed, secure, and scalable source control service that hosts private Git repositories.

Benefits of CodeCommit

* Fully managed by AWS 
* Stored encrypted and secured in AWS 
* Collaborate on code 
* No limits on file types or the size of your repositories 
* Integrate with other AWS services 
* Migrate to CodeCommit from other git repositories 
* Use the same git workflows you are familiar with

## CodeBuild

CodeBuild is a managed build service that can compile your source code, run unit tests, and produce deployment artifacts.

### Benefits of CodeBuild

* Fully managed by AWS 
* On-demand - AWS scales with your needs 
* Pre-configured environments for many popular programming languages

### CodeBuild Concepts

* Build Project - Defines how CodeBuild will run a build and answers questions like: 
  * Where is the source code? 
  * What build environment to use? 
  * What build commands to run? 
  * Where to store the output of the build? 
* Build Environment - The OS, language runtime, and tools that CodeBuild uses for the build 
* Build Spec - A YAML file that describes the collection of commands and settings for CodeBuild to run a build

![](../../.gitbook/assets/image%20%282%29.png)

## CodeStar

An AWS service for creating, managing and working with AWS projects.

### Benefits and features

* Project templates for various projects and programming languages 
* Helps manage users and the access they require to interact with AWS services \(saves you from having to create and manage IAM policies\) 
* Integrate some IDEs with CodeStar 
* Visualize and collaborate on your projects in the same place: 
  * Application activity metrics like CPU utilization 
  * JIRA Issue tracking 
  * Commit history and changes 
  * Continuous deployment details

### CodeStar integrates with other AWS services

* CodeCommit 
* CodeBuild 
* CodeDeploy 
* CodePipeline 
* CloudWatch

