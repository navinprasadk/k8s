# Day 01: Components of Kubernetes Cluster

A Kubernetes cluster is a collection of nodes that runs containerised applications, it has two main components i.e control plane and node

1.Control Plane

- Responsible for managing the cluster and workloads
- Hosts the components used to manage Kubernetes cluster
- Monitors the workload and ensures the Kubernetes cluster attains the desired state
- Interacts with the node using kubelet which is installed on each node

2.Node

- Can be either a physical machine or a virtual machine where you run the containerised workloads
- Performs the task assigned by the control plane
- Previously called minions

## Control plane components

The Control plane is made up of Kube API server, etcd, controller, scheduler and cloud controller

1.Kube API server

- Kube API server validates and configures data for the API objects
- Serves as the frontend to the Kubernetes cluster
- Implements RESTful API over the HTTP, responsible for storing API objects into a persistent storage backend

2.etcd

- Strongly consistent, distributed key-value data store where k8s store all the cluster data (configuration data, state, and metadata)
- Consistent and Distributed (If the various components are spread across multiple computing units then it is called distributed system)
key-value
- Alternatives: Apache ZooKeeper and HashiCorp Consul

3.Controller

- Controller is a control loop that watches the shared state of the cluster through the API server and makes changes attempting to move the current state towards the desired state
- Contains a collection of controllers such as replication controller, endpoints controller, namespace controller, and service accounts controller

4.Scheduler

Watches for newly created Pods with no assigned node, and selects a node for them to run on.

5.Cloud Controller (optional)

- Present only in the cloud-based Kubernetes cluster such as Azure Kubernetes Cluster, Google Kubernetes Engine, Elastic Kubernetes Service etc.,
- Connects the cluster with the cloud provider's API

## Node components

Each node in the cluster consists of kubelet, Kube proxy and container run time

1.Kubelet

- An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod
- Kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy

2.Kube proxy

- Kube Proxy is a network proxy that runs on each node in your cluster, implementing part of the Kubernetes Service concept
- Kube proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster

3.Container Run Time

- Container Run Time is the software that is responsible for running containers
- Commonly used container run time: containerd, CRI-O, Docker, Mirantis Container Runtime
