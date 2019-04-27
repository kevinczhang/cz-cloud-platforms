---
description: Simple Workflow
---

# SWF

* SWF is a fully-managed workflow service provided by AWS 
* An SWF **workflow** allows an architect/developer to implement distributed, asynchronous applications as a workflow 
* A **workflow** coordinates and manages the execution of activities that can be run asynchronously across multiple computing devices 
* SWF has consistent execution 
* SWF guarantees the order in which tasks are executed 
* There are no duplicate tasks 
* SWF is primarily an API which an application can integrate its workflow into. This allows the service to be used by non-AWS services, such as an on-premises data center 
* A workflow execution can last up to 1 year

### Components of SWF 

* **Workflows** are a sequence of steps required to perform a specific task: A workflow is also commonly referred to as a decider 
* **Activities** are a single step \(or unit of work\) in the workflow 
* **Tasks** are what interacts with the “workers” that are part of a workflow - there are two kinds of tasks: 
  * Activity task – Tells a worker to perform a function \(to encode video, check inventory etc.\) 
  * Decision task – Tells the decider the state of the work flow execution, which allows the decider to determine the next activity to be performed 
* **Workers** are responsible for receiving a task and taking action on it: Can be any type of component such as an EC2 instance, or even a person

## Simple Workflow Service and Other Services:

### SWF and SQS 

#### Similarities

* Both can be used to create distributed systems 
* Both allow each task/component to scale independently 

#### Differences: 

* SWF can have a human task as part of the workflow 
* SWF workflows and tasks last up to 1 year and SQS messages only live 14 days

### SWF and Step Functions 

#### Similarities

* Both can help create coordinating application components 

#### Differences:

* SWF uses a decider program, not a JSON-defined state machine, to make decisions 
* SWF does not have the visual workflows of Step Functions 
* SWF gives you complete control over orchestration logic but increases the complexity of your applications

