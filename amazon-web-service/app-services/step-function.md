# Step Function

AWS Step Functions is a fully-managed way to coordinate and step through your application's components. Step functions provides orchestration tools and visual workflows that can help you reliably coordinate components of your distributed applications.

* AWS Step Functions is a fully-managed service to coordinate components of your applications through individual steps 
* Step Functions provides visual workflows and tools that help you coordinate components of your distributed applications 
* Step Functions is frequently used to help orchestrate and visualize application logic in serverless applications

### Step Functions Components: 

* Tasks 
* State Machines: 
  * Defined using the JSON Amazon States Language 
  * Types of states

Benefits of Step Functions

* Managed by AWS to be scalable and highly reliable 
* Visual overview of application logic 
* Avoid coding large amouts of application logic by defining it in a JSON state machine 
* Reuse application components and edit workflows easily 
* Easily integrates with AWS services like AWS Lambda

## Tasks

All work in your state machine is done by tasks. Tasks can be an activity or Lambda function.

### An activity

* Is program code that takes input and responds using Step Functions API actions 
* Can be hosted on EC2, ECS, and even mobile devices 
* Interacts with Step Functions using API Actions like GetActivityTask, SendTaskSuccess, SendTaskFailure, and SendTaskHeartbeat API 

### A Lambda function

* Is a Serverless function that responds to your state machine tasks 
* Can be written in a variety of languages 
* Can be easily and directly integrated with Step Functions

## State Types

Step Functions coordinates your tasks through state machines. Each 'state' in a state machine makes decisions based on input, performs actions, and passes output to other states.

* States are components of your state machine: Each state has a name which must be a unique string inside that state machine 
* States can do different things in your state machine: 
  * **Task** states do some work in your state machine 
  * **Choice** states make choices between different branches of your state machine 
  * **Fail or Succeed** states stop the execution of your state machine with a failure or success 
  * **Pass** states pass their input to their output and can inject some fixed data to the process 
  * **Wait** states delay the process for a certain amount of time or to a certain date or time 
  * **Parallel** states begin parallel executions of the state machine

## Transitions:

### Basic Transitions: 

* When a state machine executes, it uses a StartAt field to select one of the states to begin with 
* The next step is definined by the "Next" field which references another state defined in the state machine 
* Certain flow-control states allow choices to determine multiple "Next" fields 
* Transitions continue until: 
  * They reach a terminal state with "Type": Succeed, "Type": Fail, or "End": true 
  * They hit a runtime error 
* State machines can only have one start state

### Input and Output: 

* Each state's input is JSON 
* State's get inputs from the previous state or, for the first state, the input is passed in at execution 
* Certain states pass through input without changing it, others modify the input 
* Task states take the input provided, send that input to a task, and then recieve output from the task to be passed along

## API Actions:

* **CreateStateMachine** - Creates a state machine: 
  * A state machine consists of a collection of states that can do work 
  * State machines are specified using a JSON-based, structured language 
* **StartExecution** - Starts a state machine execution 
* **ListExecutions** - Lists state machine executions and can use optional filters: 
  * ListExecutions is eventually consistent and may not display most recent executions 
  * You can get get additional results using the nextToken value provided in an earlier result 
* **StopExecution** - Stops a state machine execution

More API Actions: [https://docs.aws.amazon.com/step-functions/latest/apireference/API\_ListExecutions.html](https://docs.aws.amazon.com/step-functions/latest/apireference/API_ListExecutions.html)

