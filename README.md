# simplek8s
This ReadMe is for notes on what I have learned about Kubernetes, they are not structured in any form or way just for my own refernce.

## A simple K8s Overview.
Kubernetes (K8s) is a software system for running multiple containers in set of multiple machines.

## Components That help work with k8s
- `minikube` for managing containers in the virtual machines.
- `kubectl` for managing the virtual machines within the cluster.

### Commands
`minikube start` starts a virtual machine (Node) that will be our K8s cluster.
`minikube status` checks if there's any cluster started?

`kubectl apply -f <filename>` - apply the configuration specified in the yaml into minikube node. (i.e create pod, services, etc)
`kubectl get pods` - gets all objects of type Pod running.
`kubectl get services` - gets all objects of type Service running.
`minikube ip` - get the IP addresses of the minicube Node

## Kubernetes With NodePort.
Below is a typical Kubernetes cluster with that uses NodePort service as a means to expose the Pod and ultimately the container(s) in the pod to the outside world.

### Overview: 
![k8s-cluster-with-nodePort.png](./readme-assets/k8s-cluster-with-nodePort.png)

#### Components Explained:
- `A K8s cluster` is a collection of K8s Nodes within a k8s ecosystem.
- A `Node` in K8s is a VM or physical machine that can run a bunch of containers within the K8s ecosystem. Each Node has it's own set of resources like CPU, Memory, etc.
- A `Pod` in k8s is an object that is responsible for running containers. A single pod can run more than one container (we usually have one container) but we can group related containers in the same pod.
- A `NodePort` is an object that is a network service within the K8s ecosystem that is responsible for exposing the container(s) within a Pod to the outside world. A `NodePort` has a reference to the Pod it is attached to.
- A `Kube-Proxy` is a component that every Node has and it is responsible for proxying requests from outside the Node to the relevant network handler service (in this example our NodePort)
- A `Load Balancer` is the entry point of the outside request to the k8s cluster. 
- A `Master` is a control plane that has capabilities like REST APIs that allow us to configure/manage the nodes in the k8s cluster.

#### How The configure of the NodePort looks like:
The NodePort is just one of many ways to configure network into our k8s Node, below are the capabilities it offers and when to be used:

## Notes
- The ports in the k8s node (Minicube) are not exposed via localhost but we need to do `minikube ip` to get the ip to use.