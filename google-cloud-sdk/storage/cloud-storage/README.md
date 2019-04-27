---
description: >-
  A scalable, fully managed, highly reliable, and cost-efficient object / blob
  store.
---

# Cloud Storage

Good for:

* Images, pictures, and videos
* Objects and blobs
* Unstructured data

Common workloads:

* Storing and streaming multimedia
* Storage for custom data analytics pipelines
* Archive, backup, and disaster recovery

## Cloud Storage creation

### Name

Must be unique across Cloud Storage. If you're [serving website content](https://cloud.google.com/storage/docs/hosting-static-website?hl=en_GB), enter the website domain as the name.

### Default storage class

Objects added to this bucket are assigned the selected storage class by default. An object's storage class and bucket location affect its geo-redundancy, availability and costs. You can set storage classes for individual objects in gsutil.

1. Multi-Regional
2. Regional
3. Nearline
4. Coldline

![](../../../.gitbook/assets/image%20%2813%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Storage Class</th>
      <th style="text-align:left">Characteristics</th>
      <th style="text-align:left">Use Cases</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="https://cloud.google.com/storage/docs/storage-classes?hl=en_GB&amp;_ga=2.86329944.-1102600730.1554915279#multi-regional">Multi-Regional Storage</a>
      </td>
      <td style="text-align:left">
        <ul>
          <li>&gt;99.99% typical monthly availability</li>
          <li>99.95% availability SLA*</li>
          <li>Geo-redundant</li>
        </ul>
      </td>
      <td style="text-align:left">
        <p>Storing data that is frequently accessed (&quot;hot&quot; objects) around
          the world, such as serving website content, streaming videos, or gaming
          and mobile applications.</p>
        <p>For Multi-Regional Storage data stored in <a href="https://cloud.google.com/storage/docs/locations#location-dr">dual-regional locations</a>,
          you also get optimized performance when accessing Google Cloud Platform
          products that are located in one of the associated regions.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://cloud.google.com/storage/docs/storage-classes?hl=en_GB&amp;_ga=2.86329944.-1102600730.1554915279#regional">Regional Storage</a>
      </td>
      <td style="text-align:left">
        <ul>
          <li>99.99% typical monthly availability</li>
          <li>99.9% availability SLA*</li>
          <li>Lower cost per GB stored</li>
          <li>Data stored in a narrow geographic region</li>
          <li>Redundant across availability zones</li>
        </ul>
      </td>
      <td style="text-align:left">Storing frequently accessed data in the same region as your Google Cloud
        DataProc or Google Compute Engine instances that use it, such as for data
        analytics.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://cloud.google.com/storage/docs/storage-classes?hl=en_GB&amp;_ga=2.86329944.-1102600730.1554915279#nearline">Nearline Storage</a>
      </td>
      <td style="text-align:left">
        <ul>
          <li>99.95% typical monthly availability in multi-regional locations; 99.9%
            typical monthly availability in regional locations.</li>
          <li>99.9% availability SLA* in multi-regional locations; 99.0% availability
            SLA* in regional locations.</li>
          <li>Very low cost per GB stored</li>
          <li>Data retrieval costs</li>
          <li>Higher per-operation costs</li>
          <li>30-day minimum storage duration</li>
        </ul>
      </td>
      <td style="text-align:left">Data you do not expect to access frequently (i.e., no more than once per
        month). Ideal for back-up and serving long-tail multimedia content.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://cloud.google.com/storage/docs/storage-classes?hl=en_GB&amp;_ga=2.86329944.-1102600730.1554915279#coldline">Coldline Storage</a>
      </td>
      <td style="text-align:left">
        <ul>
          <li>99.95% typical monthly availability in multi-regional locations; 99.9%
            typical monthly availability in regional locations.</li>
          <li>99.9% availability SLA* in multi-regional locations; 99.0% availability
            SLA* in regional locations.</li>
          <li>Lowest cost per GB stored</li>
          <li>Data retrieval costs</li>
          <li>Higher per-operation costs</li>
          <li>90-day minimum storage duration</li>
        </ul>
      </td>
      <td style="text-align:left">Data you expect to access infrequently (i.e., no more than once per year).
        Typically this is for disaster recovery, or data that is archived and may
        or may not be needed at some future time.</td>
    </tr>
  </tbody>
</table>### Location

1. United States \(multiple regions in the United States\)
2. European Union \(multiple regions in the European Union\)
3. Asia \(multiple regions in Aisa\)
4. eur4 \(Finland and Netherlands\)
5. nam4 \(Iowa and South Carolina\)

### Access control model

#### Set permissions uniformly at bucket-level \(Bucket Policy Only\)

Enforces the bucket's IAM policy without object ACLs. May help prevent unintended access. If selected, this option becomes permanent after 90 days.

#### Set object-level and bucket-level permissions

Enforces the IAM policy and object ACLs for more granular control of object access.

### Encryption

Data is encrypted automatically. 

#### Google-managed key \(No configuration required\)

#### Customer-managed key \(Manage via Google Cloud Key Management Service\)

### Retention policy

Set a retention policy to specify the minimum duration that this bucket's objects must be protected from deletion or modification after they're uploaded. You might set a policy to address industry-specific retention challenges.



