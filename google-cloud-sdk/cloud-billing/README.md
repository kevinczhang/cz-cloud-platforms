# Cloud Billing

## Billing account & payments profile

A **billing account** is set up in GCP and is used to define who pays for a given set of GCP resources. [Access control to a billing account](https://cloud.google.com/billing/docs/how-to/billing-access) is established by Cloud Identity and Access Management \(IAM\) roles. A billing account is connected to a[**Google payments profile**](https://support.google.com/paymentscenter/topic/9017382?ref_topic=9037778) that includes a payment instrument to which costs are charged.

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

