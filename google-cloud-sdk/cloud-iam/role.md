# Role

There are three kinds of roles in Cloud IAM:

* **Primitive roles**: The roles historically available in the Google Cloud Platform Console will continue to work. These are the **Owner**, **Editor**, and **Viewer** roles.
* **Predefined roles**: Predefined roles are the Cloud IAM roles that give finer-grained access control than the primitive roles. For example, the predefined role **Pub/Sub Publisher** \(roles/pubsub.publisher\) provides access to _only_ publish messages to a Cloud Pub/Sub topic.
* **Custom roles**: Roles that you create to tailor permissions to the needs of your organization when predefined roles don't meet your needs.

To determine if one or more permissions are included in a primitive, predefined, or custom role, you can use one of the following methods:

* The [`gcloud iam roles describe`](https://cloud.google.com/sdk/gcloud/reference/iam/roles/describe) command
* The [`roles.get()`](https://cloud.google.com/iam/reference/rest/v1/roles/get) API

### Primitive roles <a id="primitive_roles"></a>

There are three roles that existed prior to the introduction of Cloud IAM: Owner, Editor, and Viewer. These roles are concentric; that is, the Owner role includes the permissions in the Editor role, and the Editor role includes the permissions in the Viewer role.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Title</th>
      <th style="text-align:left">Permissions</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>roles/viewer</code>
      </td>
      <td style="text-align:left">Viewer</td>
      <td style="text-align:left">Permissions for read-only actions that do not affect state, such as viewing
        (but not modifying) existing resources or data.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>roles/editor</code>
      </td>
      <td style="text-align:left">Editor</td>
      <td style="text-align:left">All viewer permissions, <b>plus</b> permissions for actions that modify
        state, such as changing existing resources.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>roles/owner</code>
      </td>
      <td style="text-align:left">Owner</td>
      <td style="text-align:left">
        <p>All editor permissions <b>and</b> permissions for the following actions:</p>
        <ul>
          <li>Manage roles and permissions for a project and all resources within the
            project.</li>
          <li>Set up billing for a project.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>### Predefined roles <a id="predefined_roles"></a>

Cloud IAM provides additional predefined roles that give granular access to specific Google Cloud Platform resources and prevent unwanted access to other resources. You can grant multiple roles to the same user.

#### App Engine roles <a id="app-engine-roles"></a>



| Role | Description |
| :--- | :--- |
| `roles/ appengine.appAdmin` | Read/Write/Modify access to all application configuration and settings. |
| roles/ appengine.appViewer | Read-only access to all application configuration and settings. |
| roles/ appengine.codeViewer | Read-only access to all application configuration, settings, and deployed source code. |
| roles/ appengine.deployer | Read-only access to all application configuration and settings. |
| roles/ appengine.serviceAdmin | Read-only access to all application configuration and settings. Write access to module-level and version-level settings. Cannot deploy a new version. |

#### Billing roles \(Lowest Resource: Billing Account\) <a id="billing-roles"></a>

| Role | Description |
| :--- | :--- |
| `roles/ billing.admin` | Provides access to see and manage all aspects of billing accounts. |
| roles/ billing.creator | Provides access to create billing accounts. |
| roles/ billing.projectManager | Provides access to assign a project's billing account or disable its billing. |
| roles/ billing.user | Provides access to associate projects with billing accounts. |
| roles/ billing.viewer | View billing account cost information and transactions. |

#### Cloud Build roles <a id="cloud-build-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ cloudbuild.builds.builder | Can perform builds |
| roles/ cloudbuild.builds.editor | Provides access to create and cancel builds. |
| roles/ cloudbuild.builds.viewer | Provides access to view builds. |

#### Cloud Functions roles <a id="cloud-functions-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ cloudfunctions.developer | Read and write access to all functions-related resources. |
| roles/ cloudfunctions.viewer | Read-only access to functions and locations. |

#### Cloud SQL roles <a id="cloud-sql-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ cloudsql.admin | Provides full control of Cloud SQL resources. |
| roles/ cloudsql.client | Provides connectivity access to Cloud SQL instances. |
| roles/ cloudsql.editor | Provides full control of existing Cloud SQL instances excluding modifying users, SSL certificates or deleting resources. |
| roles/ cloudsql.viewer | Provides read-only access to Cloud SQL resources. |

#### Compute Engine roles <a id="compute-engine-roles"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Role</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">roles/ compute.admin</td>
      <td style="text-align:left">Full control of all Compute Engine resources.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.imageUser</td>
      <td style="text-align:left">Permission to list and read images without having other permissions on
        the image.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.instanceAdmin.v1</td>
      <td style="text-align:left">
        <p>Full control of Compute Engine instances, instance groups, disks, snapshots,
          and images. Read access to all Compute Engine networking resources.</p>
        <p>If you grant a user this role only at an instance level, then that user
          cannot create new instances.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.loadBalancerAdmin</td>
      <td style="text-align:left">Permissions to create, modify, and delete load balancers and associate
        resources.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.networkAdmin</td>
      <td style="text-align:left">Permissions to create, modify, and delete networking resources, except
        for firewall rules and SSL certificates.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.networkUser</td>
      <td style="text-align:left">Provides access to a shared VPC network. Once granted, service owners
        can use VPC networks and subnets that belong to the host project.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.networkViewer</td>
      <td style="text-align:left">Read-only access to all networking resources</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.osAdminLogin</td>
      <td style="text-align:left">Access to log in to a Compute Engine instance as an administrator user.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.osLogin</td>
      <td style="text-align:left">Access to log in to a Compute Engine instance as a standard user.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.osLoginExternalUser</td>
      <td style="text-align:left">Available only at the organization level.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.storageAdmin</td>
      <td style="text-align:left">Permissions to create, modify, and delete disks, images, and snapshots.</td>
    </tr>
    <tr>
      <td style="text-align:left">roles/ compute.viewer</td>
      <td style="text-align:left">Read-only access to get and list Compute Engine resources, without being
        able to read the data stored on them.</td>
    </tr>
  </tbody>
</table>#### Kubernetes Engine roles <a id="kubernetes-engine-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ container.admin | Provides access to full management of Container Clusters and their Kubernetes API objects. |
| roles/ container.clusterAdmin | Provides access to management of Container Clusters. |
| roles/ container.clusterViewer | Read-only access to Kubernetes Clusters. |
| roles/ container.developer | Provides full access to Kubernetes API objects inside Container Clusters. |
| roles/ container.hostServiceAgentUser | Use access of the Kubernetes Engine Host Service Agent. |
| roles/ container.viewer | Provides read-only access to GKE resources. |

#### Datastore roles <a id="datastore-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ datastore.importExportAdmin | Provides full access to manage imports and exports. |
| roles/ datastore.indexAdmin | Provides full access to manage index definitions. |
| roles/ datastore.owner | Provides full access to Cloud Datastore resources. |
| roles/ datastore.user | Provides read/write access to data in a Cloud Datastore database. |
| roles/ datastore.viewer | Provides read access to Cloud Datastore resources. |

#### IAM roles <a id="iam-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ iam.securityReviewer | Provides permissions to list all resources and Cloud IAM policies on them. |

#### Roles roles <a id="roles-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ iam.organizationRoleAdmin | Provides access to administer all custom roles in the organization and the projects below it. |
| roles/ iam.organizationRoleViewer | Provides read access to all custom roles in the organization and the projects below it. |
| roles/ iam.roleAdmin | Provides access to all custom roles in the project. |
| roles/ iam.roleViewer | Provides read access to all custom roles in the project. |

#### Service Accounts roles <a id="service-accounts-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ iam.serviceAccountAdmin | Create and manage service accounts. |
| roles/ iam.serviceAccountCreator | Access to create service accounts. |
| roles/ iam.serviceAccountDeleter | Access to delete service accounts. |
| roles/ iam.serviceAccountKeyAdmin | Create and manage \(and rotate\) service account keys. |
| roles/ iam.serviceAccountTokenCreator | Impersonate service accounts \(create OAuth2 access tokens, sign blobs or JWTs, etc\). |
| roles/ iam.serviceAccountUser | Run operations as the service account. |

#### Storage roles <a id="storage-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ storage.admin | Grants full control of objects and buckets. |
| roles/ storage.objectAdmin | Grants full control of objects, including listing, creating, viewing, and deleting objects. |
| roles/ storage.objectCreator | Allows users to create objects. Does not give permission to view, delete, or overwrite objects. |
| roles/ storage.objectViewer | Grants access to view objects and their metadata, excluding ACLs. Can also list the objects in a bucket. |
| roles/ storagetransfer.admin | Create, update and manage transfer jobs and operations. |
| roles/ storagetransfer.user | Create and update storage transfer jobs and operations. |
| roles/ storagetransfer.viewer | Read access to storage transfer jobs and operations |

#### Stackdriver roles <a id="stackdriver-roles"></a>

| Role | Description |
| :--- | :--- |
| roles/ stackdriver.accounts.editor | Read/write access to manage Stackdriver account structure. |
| roles/ stackdriver.accounts.viewer | Read-only access to get and list information about Stackdriver account structure. |
| roles/ stackdriver.resourceMaintenanceWindow.editor | Read/write access to manage Stackdriver resource maintenance windows. |
| roles/ stackdriver.resourceMaintenanceWindow.viewer | Stackdriver Resource Maintenance Window Viewer |

#### Source roles <a id="source-roles"></a>

| Role | Description |
| :--- | :--- |
| `roles/ source.admin` | Provides permissions to create, update, delete, list, clone, fetch, and browse repositories. Also provides permissions to read and change IAM policies. |
| `roles/ source.reader` | Provides permissions to list, clone, fetch, and browse repositories. |
| `roles/ source.writer` | Provides permissions to list, clone, fetch, browse, and update repositories. |

#### Cloud Spanner roles <a id="cloud-spanner-roles"></a>

| Role | Description |
| :--- | :--- |
| `roles/ spanner.admin` | Permission to grant and revoke permissions to other principals, allocate and delete chargeable resources, issue get/list/modify operations on resources, read from and write to databases, and fetch project metadata. |
| `roles/ spanner.databaseAdmin` | Permission to get/list all Cloud Spanner resources in a project, create/list/drop databases, grant/revoke access to project databases, and read from and write to all Cloud Spanner databases in the project. |
| `roles/ spanner.databaseReader` | Permission to read from the Cloud Spanner database, execute SQL queries on the database, and view the schema. |
| `roles/ spanner.databaseUser` | Permission to read from and write to the Cloud Spanner database, execute SQL queries on the database, and view and update the schema. |
| `roles/ spanner.viewer` | Permission to view all Cloud Spanner instances and databases, but not modify or read from them. |

### Custom roles <a id="custom_roles"></a>

Custom roles are user-defined, and allow you to bundle one or more supported permissions to meet your specific needs. Custom roles are not maintained by Google; when new permissions, features, or services are added to GCP, your custom roles will not be updated automatically.

 To create a custom role, a caller must have the `iam.roles.create` permission. 

 Users who are not owners, including organization administrators, must be assigned either the Organization Role Administrator role \(`roles/iam.organizationRoleAdmin`\) or the IAM Role Administrator role \(`roles/iam.roleAdmin`\). The IAM Security Reviewer role \(`roles/iam.securityReviewer`\) enables the ability to view custom roles but not administer them.

**Unsupported or unavailable permissions**

You should also be aware that some permissions may not be visible to you or useable in a custom role.

The following Cloud IAM permissions are not supported in custom roles:

* `iam.serviceAccounts.getAccessToken`
* `iam.serviceAccounts.actAs`
* `iam.serviceAccounts.signBlob`
* `iam.serviceAccounts.signJwt`

#### Naming the role <a id="naming_the_role"></a>

The ID for a custom role must be unique. It can be up to 30 characters long and comprised of uppercase and lowercase alphanumeric characters, underscores, and periods.

The title for a custom role does not have to be unique. Therefore, the GCP Console could display more than one custom role with the same title. 

#### Testing and deploying <a id="testing_and_deploying"></a>

Custom roles include a `role.stage` property. Initially, set the stage to `ALPHA` to indicate that the role is in early development and not ready for production. Then, allow a small set of members of your organization to use the role in a few sample use cases.

When the members are happy with the newly created custom role, change the `role.stage` property to `BETA` or `GA`. In general, if your custom role references permissions for services that are in Beta, you should mark it `BETA`, not `GA`, until the service is out of Beta.

#### Disabling Custom Roles <a id="disabling_custom_roles"></a>

If you no longer wish for people in the your organization to use the role, change its `role.stage` property to `DEPRECATED`, and optionally set the `deprecation_message` to let users know what alternative roles should be used or where to get more information.

