# [Amazon EKS Workshop](https://eksworkshop.com/010_introduction/)

## Kubernetes Basics

What is K8s:
- open source container management platform
- help to run containers at scale
- provides Object and APIs for building modern applications
- utilizes declarative configuration and automation

The machines that make up a K8s cluster are called **nodes**:
- they can be
    - physical
    - virtual
- there are two types of nodes
    - Master-node type, which makes up the [Control Plane](https://eksworkshop.com/010_introduction/architecture/architecture_control/)
    - Worker-node type, which makes upd the [Data Plane](https://eksworkshop.com/010_introduction/architecture/architecture_worker/), runs the actual container images (via pods)


K8s **Objects** are entities that are used to represent the state of the cluster. An object is a **"record of intent"** - once created , the cluster does it best to ensure it exists as defined. This is known as the cluster's desired state. A desired state can describe:
- what pods are running, and on which nodes
- IP endpoint that map to a logical group of containers (services)
- how many of replicas of a container are running
- etc etc 

**K8S Object**:
- Pod: a thin wrapper around one or more containers
- DaemonSet: implements a single instance of a pod on a worker node
- Deployment: details how to roll out across versions of our application
- Replicaset: ensures a defined number of pods are always running
- Job: ensures a pod properly runs to completion
- Service: maps a fixed IP address to a logical group of pods
- Label: key/value pairs used to associate and filtering