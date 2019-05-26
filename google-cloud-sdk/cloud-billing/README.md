---
description: >-
  This section contains information on setting up and managing your billing
  account. It also describes the Google Cloud Billing API.
---

# Cloud Billing

## Resource Overview

#### What is a resource? <a id="what_is_a_resource"></a>

In the context of GCP, resource can refer to the service-level resources that are used to process your workloads \(VMs, DBs, and so on\) as well as to the account-level resources that sit above the services, such as projects, folders, and the organization.

#### What is resource management? <a id="what_is_resource_management"></a>

Resource management is focused on how you should configure and grant access to the various Cloud resources for your company/team, specifically the setup and organization of the account-level resources that sit above the service-level resources. Account-level resources are the resources involved in setting up and administering your GCP account.

#### Resource Hierarchy <a id="gcp_resource_hierarchy_overview"></a>

GCP resources are organized hierarchically. This hierarchy allows you to map your organization's operational structure to GCP, and to manage access control and permissions for groups of related resources.

![](../../.gitbook/assets/image%20%2836%29.png)

## Billing account & payments profile

A **billing account** is set up in GCP and is used to define who pays for a given set of GCP resources. [Access control to a billing account](https://cloud.google.com/billing/docs/how-to/billing-access) is established by Cloud Identity and Access Management \(IAM\) roles. A billing account is connected to a [**Google payments profile**](https://support.google.com/paymentscenter/topic/9017382?ref_topic=9037778) that includes a payment instrument to which costs are charged.

### Billing account types

There are two types of billing accounts:

* Self-serve
  * Payment instrument is a credit or debit card or ACH direct debit, [depending on availability in each country or region](https://cloud.google.com/billing/docs/resources/currency).
  * Costs are charged automatically.
  * You can sign up for self-serve accounts online.
* Invoiced
  * Payment instrument can be check or wire transfer.
  * Invoices are sent by mail or electronically.
  * You must be eligible for invoiced billing. [Learn more about invoiced billing eligibility](https://cloud.google.com/billing/docs/how-to/invoiced-billing).

### Charging cycle

Costs are charged to a billing account automatically in one of two ways:

* Monthly billing: Costs are charged on a regular monthly cycle.
* Threshold billing: Costs are charged when your account has accrued a specific amount.

Invoiced billing accounts are always billed monthly. Self-serve billing accounts can use monthly or threshold billing.[Learn more about threshold billing](https://cloud.google.com/billing/docs/how-to/billing-cycle).

## Visualize Spend Over Time with Data Studio

You can get up-to-date billing graphs throughout the day, and use labels to slice and dice your GCP bill the way you want by combining Google Cloud Platform billing export to BigQuery functionality with Google Data Studio.

