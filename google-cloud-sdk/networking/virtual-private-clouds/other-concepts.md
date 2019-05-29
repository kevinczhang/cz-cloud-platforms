# Other Concepts

## Bastion Host



## NAT Gateway - Host Isolation

An internal address translation \(NAT\) gateway instance that can route traffic from internal-only virtual machine instances to the Internet. This allows you to use one external IP address to send traffic from multiple virtual machine instances but only expose a single virtual machine to the Internet.

## FLow Logs

_VPC Flow Logs_ record a sample of network flows sent from and received by VM instances. These logs can be used for network monitoring, forensics, real-time security analysis, and expense optimization.

You can view flow logs in [Stackdriver Logging](https://cloud.google.com/logging), and you can export logs to any destination that [Stackdriver Logging export](https://cloud.google.com/logging/docs/export/configure_export_v2) supports.

Flow logs are aggregated by connection from Compute Engine VMs and exported in real time. By subscribing to Cloud Pub/Sub, you can analyze flow logs using real-time streaming APIs.

Can be enabled within the configuration of subnets.

## Pricing

#### Billed for traffic egress

* To the internet \(varied by region\)
* From one region to another \(in the same network\)
* Between zones within a region

#### Not Billed for

* Traffic ingress
* VM to VM traffic in single zone
* Traffic to GCP service \(limit may apply\)

