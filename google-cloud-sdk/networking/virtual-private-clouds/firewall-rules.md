# Firewall Rules

Each VPC network implements a distributed virtual firewall that you can configure. Firewall rules allow you to control which packets are allowed to travel to which destinations. Every VPC network has two [implied firewall rules](https://cloud.google.com/vpc/docs/firewalls#default_firewall_rules) that **block all incoming connections** and **allow all outgoing connections**.

The `default` network has [additional firewall rules](https://cloud.google.com/vpc/docs/firewalls#default_firewall_rules), including the `default-allow-internal` rule, which permit communication among instances in the network.



