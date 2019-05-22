# CodeDeploy

CodeDeploy automates deployments of your applications to EC2, Lambda, and even on-premises environments

### Benefits of CodeDeploy: 

* Automated Deployments 
* Minimize Downtime 
* Stop and Rollback 
* Centralized Control

#### CodeDeploy Examples:

![](../../.gitbook/assets/image%20%2811%29.png)

![](../../.gitbook/assets/image%20%2823%29.png)

## Deployment Types

* In-place deployment: The existing servers are updated with the new version of an application 
* Blue/green deployment \(EC2\): 
  * New application versions are deployed on a new set of instances 
  * Traffic is routed from old to new instances 
  * If there are failures, the application can fall back to the older deployment version 
* Blue/green deployment \(Lambda\): Traffic is shifted from one Lambda version to another, this can happen in multiple ways: 
  * **Canary**: A percentage of traffic is shifted to the new version CodeDeploy then waits for a specified time and shifts the rest of the traffic if it sees no errors 
  * **Linear**: Traffic is shifted in equal increments with an equal number of minutes between each increment 
  * **All at once**: Traffic is immediately and completely shifted to the new version of the Lambda function

## CodeDeploy Hooks

#### CodeDeploy AppSpec File

* Lambda Deployments: 
  * Which functions to deploy 
  * Which functions to use as validation tests 
* EC2/On-Premises Deployments: 
  * What to install \(from S3 or GitHub\) 
  * What lifecycle event hooks to run in response to deployment lifecycle events

#### Lifecycle Hooks

* Available hooks depend on the deployment type 
* Hooks allow arbitrary scripts to run during your deployment process 
* Typical examples include: 
  * BeforeInstall 
  * AfterInstall 
  * ApplicationStart 
  * ApplicationStop 
  * ValidateService 

#### For a full list and description of lifecycle hooks, check out the AWS documentation.

![](../../.gitbook/assets/image%20%281%29.png)

