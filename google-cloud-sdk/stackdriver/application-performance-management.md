# Application Performance Management

## Stackdriver Debugger

[Stackdriver Debugger](https://cloud.google.com/debugger/) lets you debug your applications while they are running in production, without stopping them or slowing them down, so you can examine your applications performance under actual production conditions.

The Stackdriver Debugger API allows applications to interact with the [Google Stackdriver Debugger](https://cloud.google.com/debugger/) backends.

It provides two interfaces: the _Debugger interface_ and the _Controller interface_. The Controller interface allows you to implement an [agent](https://cloud.google.com/debugger/api/concepts#agents) that sends state data -- for example, the value of program variables and the call stack -- to Stackdriver Debugger when the application is running. The Debugger interface allows you to implement a Stackdriver Debugger [client](https://cloud.google.com/debugger/api/concepts#debugger_clients) that allows users to set and delete the breakpoints at which the state data is collected, as well as read the data that is captured.

The Stackdriver Debugger API supports the following protocols:

* [REST](https://cloud.google.com/debugger/api/reference/rest/), which allows you to interact with the Stackdriver Debugger backends using JSON over HTTP.
* [RPC](https://cloud.google.com/debugger/api/reference/rpc/), which allows you to interact with the backends using [gRPC](http://www.grpc.io/). This API doesn't provide gRPC client libraries at this time. If you want to use this interface, you can generate gRPC client code from the [service definition](https://github.com/googleapis/googleapis/tree/master/google/devtools/clouddebugger/v2) following the instructions in the [gRPC documentation](http://www.grpc.io/).

## Stackdriver Trace

Stackdriver Trace, a distributed tracing system for Google Cloud Platform \(GCP\), helps you understand how long it takes your application to handle incoming requests from users or other applications, and how long it takes to complete operations like RPC calls performed when handling the requests.

### Components <a id="components"></a>

Stackdriver Trace consists of a tracing client, which collects the data and sends it to your GCP project, and a console interface on GCP, which lets you view and analyze the data collected by the agent.

#### Tracing client <a id="tracing_client"></a>

If you are using App Engine standard environment, you don't need to do anything. App Engine standard environment automatically captures traces and sends them to your GCP project.

If you are instrumenting your code, import the Trace SDK library then create trace data and send it to your GCP project using the Stackdriver Trace API.

#### Tracing interface <a id="tracing_interface"></a>

After the agent has collected trace data, you can view and analyze that data in near real-time in the Stackdriver Trace interface. The interface contains three windows: **Overview**, **Trace list**, and **Analysis reports**.

## Stackdriver Profiler

Stackdriver Profiler is a statistical, low-overhead profiler that continuously gathers CPU usage and memory-allocation information from your production applications. It attributes that information to the application's source code, helping you identify the parts of the application consuming the most resources, and otherwise illuminating the performance characteristics of the code.



