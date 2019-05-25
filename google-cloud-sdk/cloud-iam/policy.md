# Policy



![IAM policy](../../.gitbook/assets/image%20%289%29.png)

 A Cloud IAM policy is represented by the IAM `Policy` object. An IAM `Policy` object consists of a list of bindings. A `Binding` binds a list of `members` to a `role`.

`role` is the role you want to assign to the member. The `role` is specified in the form of `roles/<name of the role>`. For example, `roles/storage.objectAdmin`, `roles/storage.objectCreator`, and `roles/storage.objectViewer`.

`members` contains a list of one or more identities as described in the [Concepts related to identity](https://cloud.google.com/iam/docs/overview#concepts_related_identity) section above. 

The Cloud IAM methods are:

* `setIamPolicy()`: Allows you to set policies on your resources.
* `getIamPolicy()`: Allows you to get a policy that was previously set.
* `testIamPermissions()`: Allows you to test whether the caller has the specified permissions for a resource.

The following code snippet shows the structure of a Cloud IAM policy.

```text
{
  "bindings": [
   {
     "role": "roles/storage.objectAdmin",
     "members": [
       "user:alice@example.com",
       "serviceAccount:my-other-app@appspot.gserviceaccount.com",
       "group:admins@example.com",
       "domain:google.com" ]
   },
   {
     "role": "roles/storage.objectViewer",
     "members": ["user:bob@example.com"]
   }
   ]
}
```

#### Policy hierarchy <a id="policy_hierarchy"></a>

You can set a Cloud IAM policy at any level in the resource hierarchy: the organization level, the folder level, the project level, or the resource level. Resources inherit the policies of the parent resource. If you set a policy at the organization level, it is automatically inherited by all its children projects, and if you set a policy at the project level, it's inherited by all its child resources. The effective policy for a resource is the union of the policy set at that resource and the policy inherited from higher up in the hierarchy.

The Cloud IAM policy hierarchy follows the same path as the GCP resource hierarchy. If you change the resource hierarchy, the policy hierarchy changes as well. For example, moving a project into an organization will update the project's Cloud IAM policy to inherit from the organization's Cloud IAM policy.

Child policies cannot restrict access granted at a higher level.

### Cloud IAM Policies with Conditions <a id="syntax_overview"></a>

 Conditions are specified in the role bindings of a resource’s Cloud IAM policy. When a condition exists, the role is only granted if the condition expression evaluates to `true`. Each condition expression is defined as a set of logic statements allowing you to specify one or many attributes to check.

Cloud IAM policies are comprised of one or more [role bindings](https://cloud.google.com/iam/reference/rest/v1/Binding), which have the following structure:

```text
"bindings": [
  {
    "role": ...
    "members": ...
    "condition": {
      "title": ...
      "description": ...
      "expression": ...
    }
  },
  ...
]
```

The `condition` object is optional, and each role binding can contain only one. However, the condition expression can contain multiple statements that evaluate many different attributes. 

The condition's `title` is required, but the `description` is optional. Both the title and description are purely informational fields to help you identify and describe the condition. The `expression` field defines an [attribute-based](https://cloud.google.com/iam/docs/conditions-overview#attributes)logic expression using a subset of the Common Expression Language \(CEL\). For more information, see the [CEL specification](https://github.com/google/cel-spec) and its [language definition](https://github.com/google/cel-spec/blob/master/doc/langdef.md).

In general, a condition expression consists of one or more clauses that are joined using logic operators \(`&&`, `||`, or `!`\). Each clause expresses an attribute-based control rule that applies to the binding.

### Condition Attributes <a id="attributes"></a>

#### Resource Attributes <a id="resource_attributes"></a>

Resource attributes provide restrictions based on the resource in the access request, such as the resource type, resource name, or the GCP service being used.

Allow access to compute instances, but no other type of resource:

```text
resource.type == “google.cloud.compute.Instance”
```

Allow access to Cloud Storage resources, but no other service's resources:

```text
resource.service == “google.cloud.storage”
```

Allow access only to resources whose names start with a specified string:

```text
resource.name.startsWith("projects/_/buckets/exampleco-site-assets-")
```

#### Request Attributes <a id="request_attributes"></a>

Request attributes provide restrictions based on details about the access request, such as its date/time, the expected URL host/path \(for Cloud IAP\), destination IP address and port \(for Cloud IAP TCP tunneling\), or access levels.

Allow access temporarily until a specified expiration date/time:

```text
request.time < timestamp("2019-01-01T07:00:00Z")
```

Allow access only during specified working hours:

```text
request.time.getHours("Europe/Berlin") >= 9 &&
request.time.getHours("Europe/Berlin") <= 17 &&
request.time.getDayOfWeek("Europe/Berlin") >= 1 &&
request.time.getDayOfWeek("Europe/Berlin") <= 5
```

Allow access only for a specified month and year:

```text
request.time.getFullYear("Europe/Berlin") == 2018
request.time.getMonth("Europe/Berlin") < 6
```

