# Kubernetes Pods - Summary of Concepts

## Pre-requisites

## Kubernetes Automation## Single Container vs Multiple Containers in a Pod

**Single Container Pods**: This is the more common and simple use case. we'll mostly focus on Pods containing a single container.

**Multiple Containers Pods**: A less common use case where you might need both an application container and a helper container in the same Pod. This can be useful when the containers need to share resources or interact closely with each other.anual Docker Setup

In a traditional Docker setup, if you had a main container and a helper container, you'd have to manually manage their connections, networks, and shared storage.

### But With Kubernetes

You define which containers belong to the same Pod, and Kubernetes automatically manages:

- **Networking**: Containers in a Pod can easily communicate with each other.
- **Storage**: Containers in the same Pod can share volumes for storing and accessing data.
- **Lifecycle Management**: Containers in a Pod are created and destroyed together, ensuring synchronization.ages

Imagine the application has already been developed, built into Docker images, and stored in a Docker repository (e.g., Docker Hub) from where Kubernetes can pull it down.

### Kubernetes Cluster

The Kubernetes cluster is already set up and functional. It could be a single-node or multi-node setup, and all services in the cluster must be running.

### Goal of Kubernetes

The aim is to deploy your application in the form of containers across a set of machines (worker nodes) in a Kubernetes cluster.

## Kubernetes and Pods

### What is a Pod?

Pod is the smallest deployable unit in Kubernetes.

A Pod is used to encapsulate one or more containers.

While the pod can contain multiple containers, typically each pod will contain a single container (most common use case).

### Why Pods?

Kubernetes does not deploy containers directly on worker nodes. Instead, it encapsulates containers within a Pod.

This allows Kubernetes to manage, scale, and maintain the lifecycle of containers more efficiently through pods.

## Pod and Scaling

When the number of users increases and your application needs to scale, you create new Pods, not new containers within the existing pod.

You do not add more containers to an existing pod to scale up.

For example, if you need two instances of your web application, you would create two separate Pods with their own containers.

If your cluster's node has insufficient capacity, Kubernetes can deploy new Pods on a new node to scale the physical resources.

### Scaling Down

To scale down, you simply delete existing Pods. You do not remove containers from a pod.

## Multiple Containers in a Pod

While Pods usually contain a single container, there are cases where you may need multiple containers in a single Pod.

For example:

**Helper Containers**: These perform tasks that assist the main application, such as processing data or managing files.

When multiple containers are in a pod, they:

- Share the same network namespace (they can communicate using localhost).
- Share volumes (storage), which makes it easier to share data between containers.
- Have a common lifecycle — if the main container starts or stops, the helper container does the same.

Kubernetes Automation vs Manual Docker Setup:

In a traditional Docker setup, if you had a main container and a helper container, you’d have to manually manage their connections, networks, and shared storage.

But With Kubernetes:

You define which containers belong to the same Pod, and Kubernetes automatically manages:

    Networking: Containers in a Pod can easily communicate with each other.

    Storage: Containers in the same Pod can share volumes for storing and accessing data.

    Lifecycle Management: Containers in a Pod are created and destroyed together, ensuring synchronization.

Single Container vs Multiple Containers in a Pod:

Single Container Pods: This is the more common and simple use case. we’ll mostly focus on Pods containing a single container.

Multiple Containers Pods: A less common use case where you might need both an application container and a helper container in the same Pod. This can be useful when the containers need to share resources or interact closely with each other.

## Deploying Pods

### kubectl run Command

The kubectl run command is used to deploy a Pod.

This command creates a Pod and runs a container from the specified Docker image (e.g., nginx).

You must specify the image that Kubernetes will pull from a Docker repository (like Docker Hub).

### Checking Pod Status

You can see the status of your Pods using the kubectl get pods command.

Initially, the Pod may show as "ContainerCreating" and then transition to "Running" once the container is fully deployed.

## Common kubectl Commands

### To create a default pod

```bash
kubectl run nginx --image=nginx
```

### To get the pods or nodes with wide output

```bash
kubectl get pods -o wide
kubectl get nodes -o wide
```

### To describe the complete pod

```bash
kubectl describe pod nginx
```

