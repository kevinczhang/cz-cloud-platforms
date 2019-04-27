# Execution Environment

## Auto-scaling and Concurrency

Each instance of a function handles only one concurrent request at a time. This means that while your code is processing one request, there is no possibility of a second request being routed to the same instance.

In cases where inbound request volume exceeds the number of existing instances, Cloud Functions may start multiple new instances to handle requests. This automatic scaling behavior allows Cloud Functions to handle many requests in parallel, each using a different instance of your function.

Cloud Functions allows you to set a [limit on the total number of function instances](https://cloud.google.com/functions/docs/max-instances) that can co-exist at any given time. Under normal circumstances, your function scales up by creating new instances to handle incoming traffic load. But when you have set a max instances limit, you may encounter a scenario where there are insufficient instances to meet that traffic load. In that case, incoming requests queue for up to 60 seconds. During this 60 second window, if an instance finishes processing a request, it becomes available to process queued requests. If no instances become available during the 60 second window, the request fails.

## Cold starts

A new function instance is started in two cases:

* When you deploy your function.
* When a new function instance is automatically created to scale up to the load, or occasionally to replace an existing instance.

 If your code or any other code you call throws an uncaught exception or crashes the current process, then the function instance might be restarted before handling the next invocation. This can lead to more [cold starts](https://cloud.google.com/functions/docs/concepts/exec#cold_starts), resulting in higher latency, and thus is discouraged.

## Timeout

Function execution time is limited by the timeout duration, which you can specify at function deployment time. A function times out after 1 minute by default, but you can extend this period up to 9 minutes. When function execution exceeds the timeout, an error status is immediately returned. Any remaining code that is executing might be terminated.

```text
gcloud functions deploy FUNCTION_NAME --timeout=TIMEOUT FLAGS...
```



