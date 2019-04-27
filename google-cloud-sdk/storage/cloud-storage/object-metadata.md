---
description: Objects stored in Cloud Storage have metadata associated with them.
---

# Object metadata

Metadata identifies properties of the object, as well as specifies how the object should be handled when it's accessed. Metadata exists as _key:value pairs_.

## Editable metadata

#### Fixed-key metadata <a id="mutable"></a>

* **Access control metadata \(**Cloud Storage uses [Identity and Access Management \(IAM\)](https://cloud.google.com/storage/docs/access-control/iam) and [Access Control Lists \(ACLs\)](https://cloud.google.com/storage/docs/access-control/lists) to control access to objects.**\)**
* **Cache-Control \(**The `Cache-Control` metadata can specify two different aspects of how data is served from Cloud Storage: whether the data can be cached and whether the data can be transformed.**\)**
* **Content-Disposition \(**The `Content-Disposition` metadata specifies presentation information about the data being transmitted.**\)**
* **Content-Encoding \(**The `Content-Encoding` metadata can be used to indicate that an object is compressed, while still maintaining the object's underlying `Content-Type`.**\)**
* **Content-Language \(**The `Content-Language` metadata indicates the language\(s\) that the object is intended for.**\)**
* **Content-Type \(**The most commonly set metadata is `Content-Type` \(also known as MIME type\), which allows browsers to render the object properly. **\)**
* **Custom metadata \(**Custom metadata is metadata that you can add and remove. To create custom metadata, you specify both a value and a key. Once you have created a custom metadata `key:value` pair, you can delete the key or change the value.**\)**

### Non-editable metadata <a id="fixed"></a>

Some metadata cannot be edited directly. This metadata is set at the time of object creation or rewrite. As part of the object creation or rewrite, you can set some such metadata, such as the [storage class](https://cloud.google.com/storage/docs/storage-classes) of the object or [customer-supplied encryption keys](https://cloud.google.com/storage/docs/encryption/customer-supplied-keys). Other metadata is automatically added and can only be viewed, such the [generation number](https://cloud.google.com/storage/docs/key-terms#generation-numbers) of the object or the time of creation.

