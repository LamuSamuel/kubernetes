# Kubernetes Architecture

## Node

A machine that is physical or virtual , on which a kubernetes is installed.

Worker machine where containers will be launched by kubernetes.

In past Worker Node is called as minion.

When a node fails then our app fails , so its better to have more than one node.

## Cluster

It is a set of nodes grouped together. This way if one node fails, we still have access to application from other nodes

Multiple nodes can also share the traffic and workload.

### Key Questions

Who manages cluster ? where is info about members ? how are nodes monitored ? When a node fails, how do you move the workload of the failed node to another worker node?

## Master Node

The master is another node where kubernetes is installed in it and is configured as master

The master watches over the nodes in the cluster and is responsible for the actual orchestration of containers on the worker nodes.

## Components

when we install kubernetes on a system we actually installing an API server and etcd service, a Kubelet service, a container, runtime controllers and schedulers.

### API Server

Acts as a frontend for kubernetes. communication between us and k8's cluster. via cli or UI

### Etcd

(a daemon that manages configuration) : stores cluster info in form of syntax type Key value.

if we have multiple nodes and masters , etcd stores the info in a distributed manner.

Etcd is responsible for implementing locks within the cluster to ensure that there are no conflicts between the masters, Imagine you need to change a config (deployment or service) in the application you pass a cli command .

since this config is shared among the nodes , ETCD helps to make sure that no two masters are trying to change the same resource at the same time

### Scheduler

is responsible for distributing work or containers across different nodes . Looks for new containers and assign them to nodes.

### Controllers

are the brain behind orchestration : They're responsible for noticing and responding when nodes, containers, or endpoints goes down, the controllers make decisions to bring up new containers. in such cases the underlying software used to run the containers.

### Kubelet

is an agent that runs on each node , responsible to make sure that the containers are running on nodes as expected. interacts with api server and update the info about health of container to master node.

This info is gathered in stored in a key value pair on master and is based on popular ETCD.

## Master and Worker Nodes Summary

**Master Node**: Api server , ETCD , Controller and Scheduler.

**Worker Node**: Kubelet , Container's and Container runtime (Docker).



