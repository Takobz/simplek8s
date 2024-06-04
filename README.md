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

## Notes
- The ports in the k8s node (Minicube) are not exposed via localhost but we need to do `minikube ip` to get the ip to use.