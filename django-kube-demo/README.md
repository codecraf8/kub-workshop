#### 1. Kubernetes intro

1. kubectl run nginx --image=nginx:1.10.0

2. kubectl get pods

3. kubectl expose deployments nginx --port 80 --type NodePort

Behind the scene kubernetes, k8 created an external loadbalancer with a Public IP
attached to it. Any client who hits that public IP address will be routed to the
pods, behind the service.

We now, have a public IP that we can use the nginx container remotely.

4. kubectl list services


#### 2. Kubernetes pods

Pods represent a logical representation. They represent and hold a collection of
one or more containers. If you have multiple containers with a hard dependency on each other
they would be packaged together inside a single pod.

Pods also have volumes. Volumes are just data disks that live as long as the pods live,
and can be used by any other containers in that pod.

This is possible because pods provide a shared namespace for their contents. The containers inside our example pods can communicate to each other, have an IP address, and share the attached volume. 
