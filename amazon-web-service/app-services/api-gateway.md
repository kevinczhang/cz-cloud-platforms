# API Gateway

* API Gateway is a fully-managed service that allows you to create and manage your own APIs for your application 
* API Gateway acts as a "front door" for you application, allowing access to data/logic/functionality from your back-end services

### API Gateway Main Features:

* Build RESTful APIs with: 
  * Resources 
  * Methods \(i.e. GET, POST, PUT\) 
  * Settings 
* Deploy APIs to a "Stage" \(different envs: i.e., dev, beta, production\): Each stage can have its own throttling, caching metering, and logging 
* Create a new API version by cloning an existing one: You can create and work on multiple versions of an API \(API version control\) 
* Roll back to previous API deployments: A history of API deployments are kept 
* Custom domain names: Custom domain names can point to an API or Stage 
* Create and manage API keys for access AND meter usage of the API keys through Amazon CloudWatch Logs: 
* Set throttling rules based on the number of request per second \(for each HTTP method\): Request over the limit throttled \(HTTP 429 response\) 
* Security using Signature v.4 to sign and authorize API calls: Temporary credentials generated through Amazon Cognito and Security Token Service \(STS\)

### Benefits of API Gateway:

* Ability to cache API responses 
* DDoS protection via CloudFront 
* SDK generation for iOS, Android, and JavaScript 
* Supports Swagger \(a very popular framework of API dev tools\) 
* Request/response data transformation \(i.e. JSON IN to XML OUT\)

## API Gateway Resources:

Resources are logical entities that can be accessed via resource paths. For example, a /songs resource could be the path of a resource representing available song data.

### Resource URLs: 

* Resource URLs or URL paths are used to expose resources 
* API Gateway Resource URLs usually look something like this: [https://1ex2a3mpl4e.execute-api.us-east-1.amazonaws.com/dev/cars](https://1ex2a3mpl4e.execute-api.us-east-1.amazonaws.com/dev/cars) 
* The stage appears in the default API Endpoint: [https://1ex2a3mpl4e.execute-api.us-east-1.amazonaws.com/mystage/cars](https://1ex2a3mpl4e.execute-api.us-east-1.amazonaws.com/mystage/cars) 
* Custom API domains can simplify the URL: [https://api.mycarcompany.com/mystage/cars](https://api.mycarcompany.com/mystage/cars) 
* Resources can have child resources: [https://1ex2a3mpl4e.execute-api.us-east-1.amazonaws.com/mystage/cars/parts](https://1ex2a3mpl4e.execute-api.us-east-1.amazonaws.com/mystage/cars/parts) 
* Both resources and child resources have associated HTTP methods

## API Gateway Methods:

* API Gateway Methods are HTTP methods associated with an API Gateway Resource 
* Each resource URL can have HTTP methods like: GET, PUT, POST, DELETE 
* AWS also offers ANY as a catch-all method 
* Methods can be configured to respond to requests in a variety of ways: 
  * Lambda Functions:
    * Lambda Proxy integrations allow request data to be passed to Lambda as event 
  * Existing HTTP Endpoints 
  * Integrated with other AWS services

### Example Workflow

* A user-facing application includes an API Gateway endpoint URL within the application 
* An HTTP GET request is made to an API Gateway endpoint resource URL 
* The resource URL maps the GET request to the relevant GET method 
* In this scenario, the GET method is configured with a Lambda Proxy integration: 
  * API Gateway passes the data from the request as an event to a Lambda Function 
  * Lambda processes the request and returns a response through API Gateway 
* API Gateway returns the response from Lambda to the caller 
* The application receives the data and displays it to the user

## API Gateway Deployments and Stages:

#### Deployments: 

* Are snapshot of the API's resources and methods 
* Must be created and associated with a stage in order for anyone to access the API 

#### Stages: 

* Are references to a lifecycle status of your API such as 'dev', 'prod', or 'beta' 
* Can be mapped to deployments in order to have a functional API 
* Settings on a stage can be used to do things like: 
  * Enable caching 
  * Customize request throttling 
  * Configure logging 
  * Define stage variables

## API Gateway Caching:

* API Gateway will cache API responses so that duplicate API requests do not have to hit your back-end: 
  * Reduces load on your back-end 
  * Speeds up calls to your back-end 
* You can configure a cache key and Time to Live \(TTL\) of the API response 
* Caching can be setup on a per API or per stage basis

## API Gateway: CloudWatch

* CloudWatch can be used to monitor API Gateway activity and usage 
* Monitoring can be done on the API or Stage level 
* Throttling rules are monitored by CloudWatch 
* Monitoring metrics include such statistics as: 
  * Caching 
  * Latency 
  * Detected errors 
* Method-level metrics can be monitored 
* You can create CloudWatch alarms based on these metrics

