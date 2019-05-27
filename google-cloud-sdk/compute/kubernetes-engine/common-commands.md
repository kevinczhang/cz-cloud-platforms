# Deploying a container application

## Objectives

To package and deploy your application on GKE, you must:

1. Package your app into a Docker image
2. Run the container locally on your machine \(optional\)
3. Upload the image to a registry
4. Create a container cluster
5. Deploy your app to the cluster
6. Expose your app to the Internet
7. Scale up your deployment
8. Deploy a new version of your app

## Step 1: Build the container image

To download the `hello-app` source code, run the following commands:

```text
git clone https://github.com/GoogleCloudPlatform/kubernetes-engine-samples
cd kubernetes-engine-samples/hello-app
```

Set the `PROJECT_ID` environment variable in your shell by retrieving the pre- configured project ID on `gcloud` by running the command below:

```text
export PROJECT_ID="$(gcloud config get-value project -q)"
```

The value of `PROJECT_ID` will be used to tag the container image for pushing it to your private [Container Registry](https://cloud.google.com/container-registry).

To build the container image of this application and tag it for uploading, run the following command:

```text
docker build -t gcr.io/${PROJECT_ID}/hello-app:v1 .
```

You can run `docker images` command to verify that the build was successful:

```text
docker images
```

Output:

```text
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
gcr.io/my-project/hello-app    v1                  25cfadb1bf28        10 seconds ago      54 MB
```

## Step 2: Upload the container image

You need to upload the container image to a registry so that GKE can download and run it.

First, configure Docker command-line tool to authenticate to [Container Registry](https://cloud.google.com/container-registry) \(you need to run this only once\):

```text
gcloud auth configure-docker
```

You can now use the Docker command-line tool to upload the image to your Container Registry:

```text
docker push gcr.io/${PROJECT_ID}/hello-app:v1
```

## Step 3: Run your container locally \(optional\)

To test your container image using your local Docker engine, run the following command:

```text
docker run --rm -p 8080:8080 gcr.io/${PROJECT_ID}/hello-app:v1
curl http://localhost:8080
```

## Step 4: Create a container cluster

Run the following command to create a two-node cluster named `hello-cluster`:

```text
gcloud container clusters create hello-cluster --num-nodes=2
```

It may take several minutes for the cluster to be created. Once the command has completed, run the following command and see the cluster’s three worker VM instances:

```text
gcloud compute instances list
```

> **Note:** If you are using an existing Google Kubernetes Engine cluster or if you have created a cluster through Google Cloud Platform Console, you need to run the following command to retrieve cluster credentials and configure `kubectl` command-line tool with them:
>
> ```text
> gcloud container clusters get-credentials hello-cluster
> ```

## Step 5: Deploy your application

To deploy and manage applications on a GKE cluster, you must communicate with the Kubernetes cluster management system. You typically do this by using the `kubectl` command-line tool.

Kubernetes represents applications as [Pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/), which are units that represent a container \(or group of tightly-coupled containers\). The Pod is the smallest deployable unit in Kubernetes. In this tutorial, each Pod contains only your `hello-app` container.

The `kubectl run` command below causes Kubernetes to create a [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) named `hello-web` on your cluster. The Deployment manages multiple copies of your application, called replicas, and schedules them to run on the individual nodes in your cluster. In this case, the Deployment will be running only one Pod of your application.

Run the following command to deploy your application, listening on port 8080:

```text
kubectl run hello-web --image=gcr.io/${PROJECT_ID}/hello-app:v1 --port 8080
```

To see the Pod created by the Deployment, run the following command:

```text
kubectl get pods
```

## Step 6: Expose your application to the Internet

```text
kubectl expose deployment hello-web --type=LoadBalancer --port 80 --target-port 8080
```

The `kubectl expose` command above creates a [Service](https://kubernetes.io/docs/user-guide/services/) resource, which provides networking and IP support to your application's Pods. GKE creates an external IP and a Load Balancer \([subject to billing](https://cloud.google.com/compute/pricing#lb)\) for your application.

The `--port` flag specifies the port number configured on the Load Balancer, and the `--target-port` flag specifies the port number that is used by the Pod created by the `kubectl run` command from the previous step.

> **Note:** GKE assigns the external IP address to the **Service** resource—not the Deployment. If you want to find out the external IP that GKE provisioned for your application, you can inspect the Service with the `kubectl get service` command:
>
> ```text
> kubectl get service
> ```
>
> Output:
>
> ```text
> NAME         CLUSTER-IP      EXTERNAL-IP     PORT(S)          AGE
> hello-web    10.3.251.122    203.0.113.0     80:30877/TCP     3d
> ```

## Step 7: Scale up your application

You add more replicas to your application's Deployment resource by using the `kubectl scale` command. To add two additional replicas to your Deployment \(for a total of three\), run the following command:

```text
kubectl scale deployment hello-web --replicas=3
```

You can see the new replicas running on your cluster by running the following commands:

```text
kubectl get deployment hello-web
```

Output:

```text
NAME        DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
hello-web   3         3         3            2           1m
```

## Step 8: Deploy a new version of your app

GKE's rolling update mechanism ensures that your application remains up and available even as the system replaces instances of your old container image with your new one across all the running replicas.

You can create an image for the v2 version of your application by building the same source code and tagging it as v2 \(or you can change the `"Hello, World!"` string to `"Hello, GKE!"` before building the image\):

```text
docker build -t gcr.io/${PROJECT_ID}/hello-app:v2 .
```

Then push the image to the Google Container Registry:

```text
docker push gcr.io/${PROJECT_ID}/hello-app:v2
```

Now, apply a rolling update to the existing deployment with an image update:

```text
kubectl set image deployment/hello-web hello-web=gcr.io/${PROJECT_ID}/hello-app:v2
```

Visit your application again at `http://[EXTERNAL_IP]`, and observe the changes you made take effect.

## Cleaning up

To avoid incurring charges to your Google Cloud Platform account for the resources used in this tutorial:

After completing this tutorial, follow these steps to remove the following resources to prevent unwanted charges incurring on your account:

1. **Delete the Service:** This step will deallocate the Cloud Load Balancer created for your Service:

   ```text
   kubectl delete service hello-web
   ```

2. **Delete the container cluster:** This step will delete the resources that make up the container cluster, such as the compute instances, disks and network resources.

   ```text
   gcloud container clusters delete hello-cluster
   ```

## Quick start

#### To create a cluster, run the following command:

```text
gcloud container clusters create [CLUSTER_NAME]
```

where `[CLUSTER_NAME]` is the name you choose for the cluster.

#### To authenticate for the cluster, run the following command:

```text
gcloud container clusters get-credentials [CLUSTER_NAME]
```

This command configures `kubectl` to use the cluster you created.

#### To run `hello-app` in your cluster, run the following command:

```text
kubectl run hello-server --image gcr.io/google-samples/hello-app:1.0 --port 8080
```

#### To expose your application, run the following [`kubectl expose`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#expose) command:

```text
kubectl expose deployment hello-server --type LoadBalancer \
  --port 80 --target-port 8080
```

#### Inspect the `hello-server` Service by running [`kubectl get`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get):

```text
kubectl get service hello-server
```

#### Delete the application's Service by running [`kubectl delete`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#delete):

```text
kubectl delete service hello-server
```

#### Delete your cluster by running [`gcloud container clusters delete`](https://cloud.google.com/sdk/gcloud/reference/container/clusters/delete):

```text
gcloud container clusters delete [CLUSTER_NAME]
```

