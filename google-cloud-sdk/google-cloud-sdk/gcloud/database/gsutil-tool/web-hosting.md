---
description: web - Set a main page and/or error page for one or more buckets
---

# Web Hosting

```text
gsutil web set [-m main_page_suffix] [-e error_page] bucket_url...
gsutil web get bucket_url
```

The Website Configuration feature enables you to configure a Cloud Storage bucket to behave like a static website. This means requests made via a domain-named bucket aliased using a Domain Name System "CNAME" to c.storage.googleapis.com will work like any other website, i.e., a GET to the bucket will serve the configured "main" page instead of the usual bucket listing and a GET for a non-existent object will serve the configured error page.

## cors - Get or set a CORS JSON document for one or more buckets

```text
gsutil cors set cors-json-file url...
gsutil cors get url
```

