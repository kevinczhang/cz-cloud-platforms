# Export Billing

## Export Billing Data to a File

To access a detailed breakdown of your charges, you can export your daily usage and cost estimates automatically to a CSV or JSON file stored in a [Google Cloud Storage](https://cloud.google.com/storage/index) bucket you specify.

### How to enable billing export to a file <a id="how_to_enable_billing_export_to_a_file"></a>

To enable billing export:

1. If you haven't already created a bucket in Google Cloud Storage, you need to create one. For instructions, see[Creating Storage Buckets](https://cloud.google.com/storage/docs/creating-buckets).
2. Then to enable billing export, go to the [Google Cloud Platform Console](https://console.cloud.google.com/).
3. Open the left side menu and select **Billing**.
4. If you have more than one billing account, select **Go to linked billing account** to manage the current project's billing. To locate a different billing account, select **Manage billing accounts**.
5. Click **Billing export**.
6. Select **File export**.
7. For **Bucket name**, specify name of the Cloud Storage bucket into which billing reports will be exported. The Google Service Account is granted write access to this bucket.
8. For **Report prefix**, specify a prefix for the Cloud Storage object name for the exported reports. The year, month, and day is appended to the prefix.
9. For **Format**, select **CSV** or **JSON**.
10. Click **Enable billing export**.

## Export Billing Data to BigQuery

 Billing export to [BigQuery](https://cloud.google.com/bigquery) enables you to export your daily usage and cost estimates automatically throughout the day to a BigQuery dataset you specify. 

If you use regular file export, you should be aware that regular file export captures a smaller dataset than export to BigQuery.



* [Cloud Billing](https://cloud.google.com/billing/)
* *  [Documentation](https://cloud.google.com/billing/docs/)

## Export Billing Data to BigQuery

Tools for monitoring, analyzing and optimizing cost have become an important part of managing development. Billing export to [BigQuery](https://cloud.google.com/bigquery) enables you to export your daily usage and cost estimates automatically throughout the day to a BigQuery dataset you specify. You can then access your billing data from BigQuery. You can also use this export method to export data to a JSON file.

[Regular file export](https://cloud.google.com/billing/docs/how-to/export-data-file) to CSV and JSON is also available. However, if you use regular file export, you should be aware that regular file export captures a smaller dataset than export to BigQuery. For more information about regular file export and the data it captures, see [Export Billing Data to a File](https://cloud.google.com/billing/docs/how-to/export-data-file).

### How to enable billing export to BigQuery <a id="how_to_enable_billing_export_to"></a>

To enable billing export to BigQuery:

1. Go to the [Google Cloud Platform Console](https://console.cloud.google.com/).
2. Open the left side menu and select **Billing**.
3. If you have more than one billing account, select **Go to linked billing account** to manage the current project's billing. To locate a different billing account, select **Manage billing accounts**.
4. Click **Billing export**.
5. Select **BigQuery export**.
6. From the **Project** list, select the project where your BigQuery dataset is stored. If you don't have a BigQuery dataset created yet, you'll be prompted to create one.
7. If necessary, to create a new dataset:
   1. In the [BigQuery web UI](https://bigquery.cloud.google.com/), click the down arrow next to your project name, then click **Create new dataset**.
   2. Specify the **Dataset ID**, **Data location**, and **Data expiration** for your dataset, then click **OK**.
8. In the console, from the **Billing export dataset** list, specify a dataset to export data to. If you just created a dataset, choose the name of your new dataset.
9. Click **Enable BigQuery export**.

