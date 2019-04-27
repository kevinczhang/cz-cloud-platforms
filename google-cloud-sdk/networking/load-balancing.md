# Load Balancing

### Summary of Cloud load balancers <a id="summary_of_cloud_load_balancers"></a>

The following table provides some specifics about each load balancer.

| Load balancer | Traffic type | Global/Regional | External/Internal | External Ports for Load Balancing |
| :--- | :--- | :--- | :--- | :--- |
| HTTP\(S\) | HTTP or HTTPS | Global | External | HTTP on 80 or 8080; HTTPS on 443 |
| SSL Proxy | TCP with SSL offload | Global | External | 25, 43, 110, 143, 195, 443, 465, 587, 700, 993, 995, 1883, and 5222 |
| TCP Proxy | TCP without SSL offload. Does not preserve client IP addresses | Global | External | 25, 43, 110, 143, 195, 443, 465, 587, 700, 993, 995, 1883, 5222 |
| Network TCP/UDP | TCP/UDP without SSL offload. Preserves client IP addresses. | Regional | External | Any |
| Internal TCP/UDP | TCP or UDP | Regional | Internal | Any |

