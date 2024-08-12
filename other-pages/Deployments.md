# Deployments
A Deployment is a Kubernetes object that has a set of identical Pods. The Deployment is responsible for monitoring the Pods within itself and making sure they are always up with the desired state specified in the configuration file.

## How A Typical Deployment Looks Like:
to-insert-image-here

## Deployment Configuration file:
Please see the [client-deployment.yaml](../client-deployment.yaml) for the full configuration file referenced here.  

The components from the configuration file are as follows:
- `kind: Deployment` - This tells Kubernetes that the configuration file is creating a Deployment object.
- `spec -> replicas: 1` - Tells the Deployment object that it will be monitoring one Pod. This is a positive integer.
- `selector -> matchLabels -> component : web` - The selector the Deployment object will use to identify Pods that it should manage.
- `template` - Specifies the template for Pods that the Deployment will be managing.
- `template -> metadata -> labels` - Specifies a label that will given to Pods that are going to be created by this template. **This should ideally be the same as the selector -> matchLables value(s)**.
- `template -> spec` - Specifies the configuration of the containers that will be running with the Pods that the Deployment will be managing.

> [!NOTE]
> All the Pods that will be managed by this Deployment will be running the same containers with the same configuration defined the template -> spec section, thus we say the Pods that are under the same Deployment are identical.

## How The Deployment Handles Changes.
to expand on this.

