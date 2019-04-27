# Access Control

## Access control for users

Cloud Functions supports the [primitive roles](https://cloud.google.com/iam/docs/understanding-roles#primitive_roles) **Editor**, **Owner**, and **Viewer**, which grant the following permissions:

* **Editor** and **Owner**: Read and write access to all functions-related resources. Allows users to deploy, update, and delete functions. Additional access to other resources in the project.
* **Viewer**: Read-only access to functions and locations. Allows users to list functions and see their details, but does not allow them to view the source code. Additional access to other resources in the project.

Cloud Functions also supports the Cloud Functions [curated roles](https://cloud.google.com/functions/docs/reference/iam/roles) **Developer** and **Viewer**, which grant the following permissions:

* **Developer**: Read and write access to all functions-related resources. Allows users to deploy, update, and delete functions. No access to other resources in the project.
* **Viewer**: Read-only access to functions and locations. Allows users to list functions and see their details, but does not allow them to view the source code. No access to other resources in the project.

### Runtime service account <a id="runtime_service_account"></a>

 At runtime, Cloud Functions defaults to using the App Engine default service account \(`PROJECT_ID@appspot.gserviceaccount.com`\), which has the **Editor** role on the project. 

### Cloud Functions service account <a id="cloud_functions_service_account"></a>

For administrative actions on your project during the creation, updating, or deletion of functions, the Cloud Functions service uses the Google Cloud Functions service agent service account \(`service-PROJECT_NUMBER@gcf-admin-robot.iam.gserviceaccount.com`\).

By default, this service account has the **cloudfunctions.serviceAgent** role on your project. Creating, updating, and deleting functions may fail if you change this account's permissions.



