# gcloud auth

### Connect

```text
gcloud auth application-default login
```

### Listing accounts <a id="listing_accounts"></a>

```text
gcloud auth list
```

### Revoking credentials for an account <a id="revoking_credentials_for_an_account"></a>

To revoke credentials, run: [`gcloud auth revoke`](https://cloud.google.com/sdk/gcloud/reference/auth/revoke):

```text
gcloud auth revoke [ACCOUNT]
```

## GKE related

#### Push the container to the Google Cloud Container Registry. Kubernetes works with container images, not dockerfiles. So we need to build the image and put it someplace that it can be accessed.

```text
gcloud auth configure-docker -q
```

#### The tag la-ace-products:0.1 is set in the build file. If you change it here, change it there to match.

```text
docker tag la-ace-products:0.1 "gcr.io/$PROJECT_NAME/products"
docker push "gcr.io/$PROJECT_NAME/products"
```

#### Authenticate kubectl

```text
gcloud container clusters get-credentials $PRODUCT_CLUSTER_NAME --zone $PROJECT_ZONE --project $PROJECT_NAME
```



