# CodePipeline

A continuous delivery service that can model, visualize and automate your software release process.

## Benefits of CodePipeline

* Automate release processes - source repository through build, test and deploy 
* Consistent release process - define the set of steps before new changes are released 
* Real-time status of the process - view alerts, retry actions, manually rerun any pipelines 
* Tooling integrations for: 
  * Source Control - S3, CodeCommit, GitHub 
  * Build - AWS CodeBuild, CloudBees, Jenkins, SolanoCI, TeamCity 
  * Test - CodeBuild, HOE StormRunner Load, BlazeMeter, Nouvola, Runscope, Ghost Inspector 
  * Deploy - CloudFormation, CodeDeploy, ECS, Elastic Beanstalk, OpsWorks Stacks, XebiaLabs

## CopePipeline Concepts

* Pipelines - Are a workflow that describes how software changes go through release processes 
* Artifacts - Files or changes that will be worked on by the actions and stages in the pipeline 
* Stages - Pipelines are broken up into stages, for example: 
  * Build stage - where the code is built and tests are run 
  * Deployment stage - updates deployed to environments 
* Actions - Stages contain at least one action, these actions take some action on artifacts and will have artifacts as either an input an output or both 
* Transitions - The progressing from one stage to another inside of a pipeline

![](../../.gitbook/assets/image%20%287%29.png)

