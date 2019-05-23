---
description: 'get, describe, exec, run, delete'
---

# kubectl

## Pod & Container

```text
# List the current pods
kubectl get pods
# Describe pod <name>
kubectl describe pod <name>
# List the replication controllers
kubectl get rc
# List the replication controllers in <namespace>
kubectl get rc --namespace="<namespace>"
# Describe replication controller <name>
kubectl describe rc <name>
# List the services
kubectl get svc
# Describe service <name>
kubectl describe svc <name>
# Delete pod <name>
kubectl delete pod <name>
# Watch nodes continuously
kubectl get nodes –w
```

## Cluster

```text
# Get version information
kubectl version
# Get cluster information
kubectl cluster-info
# Get the configuration
kubectl config view
# Output information about a node
kubectl describe node <node>
```

## Debugging

```text
# Execute <command> on <service> optionally #
selecting container <$container>
kubectl exec <service> <command> [-c <$container>]
# Get logs from service <name> optionally # selecting
container <$container>
kubectl logs -f <name> [-c <$container>]
# Watch the Kubelet logs
watch -n 2 cat /var/log/kublet.log
# Show metrics for nodes
kubectl top node
# Show metrics for pods
kubectl top pod
```

## Quick Commands

```text
# Launch a pod called <name>
# using image <image-name>
kubectl run <name> --image=<image-name>
# Create a service described # in <manifest.yaml>
kubectl create -f <manifest.yaml>
# Scale replication controller
# <name> to <count> instances
kubectl scale --replicas=<count> rc <name>
# Map port <external> to # port <internal> on replication
# controller <name>
kubectl expose rc <name> --port=<external> --targetport=<internal>
# Stop all pods on <n>
kubectl drain <n> --delete-local-data --force --ignoredaemonsets
# Create namespace <name>
kubectl create namespace <namespace>
# Allow Kubernetes master nodes to run pods
kubectl taint nodes --all node-role.kubernetes.io/master-
```

