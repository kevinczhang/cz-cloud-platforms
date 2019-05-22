---
description: >-
  Cloud DNS is a high-performance, resilient, global Domain Name System (DNS)
  service that publishes your domain names to the global DNS in a cost-effective
  way.
---

# Cloud DNS

DNS is a hierarchical distributed database that lets you store IP addresses and other data, and look them up by name. Cloud DNS lets you publish your zones and records in the DNS without the burden of managing your own DNS servers and software.

Cloud DNS offers both public and private managed DNS zones. A public zone is visible to the public Internet, while a private zone is visible only from one or more VPC networks that you specify.

#### Managed zones

The managed zone holds DNS records for the same DNS name suffix \(`example.com`, for example\). A project can have multiple managed zones, but they must each have a unique name.

#### Public zones

A public zone is visible to the Internet. Cloud DNS has public authoritative name servers that respond to queries about public zones regardless of where the queries originate. 

#### Private zones

Private zones enable you to manage custom domain names for your virtual machines, load balancers, and other GCP resources without exposing the underlying DNS data to the public Internet. A private zone is a container of DNS records that can only be queried by one or more VPC networks that you authorize.

#### SOA serial number format

The serial numbers of SOA records created in Cloud DNS managed zones monotonically increase with each transactional change to a zone's record sets made using the `gcloud dns record-sets transaction` command. 

#### DNSSEC

The [Domain Name System Security Extensions \(DNSSEC\)](https://cloud.google.com/dns/docs/dnssec) is a suite of Internet Engineering Task Force \(IETF\) extensions to DNS which authenticate responses to domain name lookups. DNSSEC does not provide privacy protections for those lookups, but prevents attackers from manipulating or poisoning the responses to DNS requests.

#### DNSKEYs collection

The DNSKEYs collection holds the current state of the DNSKEY records used to sign a DNSSEC-enabled managed zone. You can only read this collection; all changes to the DNSKEYs are made by Cloud DNS. The DNSKEYs collection has all the information that domain registrars require to [activate DNSSEC](https://cloud.google.com/dns/docs/registrars#add-ds).

## Creation

### Create a new record <a id="create_a_new_record"></a>

Create a new record to point the domain to an external IP address.

* If your IP address is in the form `#.#.#.#`, you have an IPv4 address and need to create an `A` record. 
* If your IP address is in the format `#:#:#:#:#:#:#:#`, you have an IPv6 address and need to create an `AAAA` record.
