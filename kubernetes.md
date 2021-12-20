---
description: Introduction to Kubernetes
---

# Kubernetes

## Why choose Kubernetes?

- An open-source system for automating deployment, scaling, and management of
  containerized applications.
- No Vendor Lock-In
- Large Community of support
- Robust platform for container orchestration
- Based on 15 years of experience of running production workloads at Google,
  combined with best-of-breed ideas and practices from the community

### Kubernetes is an Orchestration Platform

- Scheduling: decide where containers run
- Lifecycle and Health: keep containers running and restart them if they fail
- Scaling: grow and shrink deployments as needed
- Naming and Discovery: help containers find each other
- LoadBalancing: distribute traffic across containers ...and a whole lot more

### Why Do You Need Container Orchestration?

- Deploy applications to servers without worrying about specific servers
- Scale the application horizontally up and dow
- This is called container auto-healing or Restore the application if the server
  on which it worked fails rescheduling

### Kubernetes has a Declarative API

Kubernetes is a Declarative Model

You express the desired state

Kubernetes maintains it

What could be simpler?

## Kubernetes Architecture

- There can be one or more Master Nodes (HA)
- There can be zero or more Worker Nodes
- Everyone communicates via the API Server
- Kubelet on each Worker Node acting as an agent
- Everything can be on one node for development use

### Kubernetes All-In-One

- You can run Kubernetes all in one VM for development work (not for
  production!)
- MiniKube is great for setting this up
- MiniShift will deploy a development version of RedHat OpenShift 3.x which uses
  Kubernetes
- CRC (Code Ready Container) will deploy OpenShift 4.x

### Kubernetes is the new "Cloud OS"

Managing Containers with VMs:

- SysAdmins must decide where to place container
- Workload balancing is manual

Managing Containers with Kubernetes:

- Kubernetes schedules and optimizes workloads automatically

## Kubernetes Pods

- Containers run in Pods
- The Pod is the smallest deployment possible
- Containers are deployed from a container registry (public or private)

## Kubernetes ReplicaSets

- ReplicaSets allow multiple copies of containers to be deployed
- Each one in it's own Pod
- If a container dies, the ReplicaSet will spawn a new one

## Kubernetes Volume Mounts

Volumes

- **ConfigMaps** hold configuration parameters
- **Secrets** hold credentials and other secrets
- **Persistent Volume Claims** are used to ask for persistent storage for
  data/state

## Kubernetes Deployments

Deployment

- Sets up the ReplicaSets for you
- Also specified the Secrets, ConfigMaps, and Volume Mounts
- Provides features for rolling out updates and handling their rollbacks

## Kubernetes Service

Service exposes Pods to the outside as:

- ClusterIP
- NodePort
- Load Balancer

### Types of Services

- **LoadBalancer**: Only available via cloud providers. Front end for service
  that balances the load across multiple backends from a single IP address
- **NodePort**: Exposes the service as an arbitrary port on every worker node in
  the cluster
- **ClusterIP**: Service is only accessible from other services within the
  cluster (no external exposure)

## Kubernetes Ingress Controller

Ingress

- Exposes Service outside of Kubernetes
- Maps URL paths to services

## Services Map to Pods via Labels

![Services Map to Pods via Labels](.gitbook/assets/services-map-to-pods-via-labels.png)

### Use Case for Multiple Containers in a Pod

Pods can be used to host vertically integrated application stacks (e.g. LAMP),
but their primary motivation is to support co-located, co-managed helper
programs, such as:

- Content management systems, file and data loaders, local cache managers, etc.
- Log and checkpoint backup, compression, rotation, snapshotting, etc.
- Data change watchers, log tailers, logging and monitoring adapters, event
  publishers, etc.
- Proxies, bridges, and adapters
- Controllers, managers, configurators, and updaters

### Linking Service to Pods

Service:

```yaml
apiVersion: v1
  kind: Service
  metadata:
    name: hitcounter-service
  spec:
    type: NodePort
    selector:
      app: hitcounter # label
    ports:
      - name: primary
        protocol: TCP
        port: 8080
```

Deployment:

```yaml
apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: hitcounter
  spec:
    replicas: 3
    selector:
      matchLabels:
        app: hitcounter # <-- should match this label
    template:
      metadata:
        labels:
          app: hitcounter
    spec:
      containers:
      - image: hitcounter:1.0
        imagePullPolicy: IfNotPresent
        name: hitcounter
        ports:
        - containerPort: 8080
        - protocol: TCP
      restartPolicy: Always
```

## Service Discovery

Kubernetes provides internal routing so services can find each other

![Internal Service Discovery](.gitbook/assets/kubernetes-internal-routing.png)

## External Service Access

LoadBalancers provide external access for a single service

![LoadBalancer](.gitbook/assets/kubernetes-external-service-access.png)

## External Routing

Kubernetes provides an **Ingress Controller** to allow external network access
or you can use NodePorts.

![External Routing](.gitbook/assets/kubernetes-external-routing.png)

### Ingress Example

```yaml
apiVersion: extensions/v1beta1
  kind: Ingress
  metadata:
    name: ecommerce
  spec:
    rules:
    - host: ecommerce.containers.mybluemix.net
      http:
        paths:
        - path: /shopcarts
          backend:
            serviceName: shopcart-service
            servicePort: 5000
        - path: /catalog
          backend:
            serviceName: catalog-service
            servicePort: 5000
        - path: /orders
          backend:
            serviceName: order-service
            servicePort: 5000
        - path: /recommendations
          backend:
            serviceName: recommendation-service
            servicePort: 5000
```

### Ingress Controller

Single entry point into multiple kubernetes services

![Ingress Controller](.gitbook/assets/kubernetes-ingress-controller.png)

## Persistent Volumes

- Kubernetes loosely couples physical storage devices with containers by
  introducing an intermediate resource called persistent volume claims (PVCs).
- A PVC defines the disk size, disk type (ReadWriteOnce, ReadOnlyMany,
  ReadWriteMany) and dynamically links a storage device to a volume defined
  against a pod
- The binding process can either be done in a static way using PVs or
  dynamically be using a persistent storage provider

### Example Volume Mount

There is a volume named `redis-storage` and that is connected to the `redis`
container via the VolumeMount: `/data/redis`

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: redis
spec:
  containers:
    - name: redis
      image: redis
      volumeMounts:
        - name: redis-storage
          mountPath: /data/redis
  volumes:
    - name: redis-storage
      emptyDir: {}
```

## Configurations Management: ConfigMaps

- Containers generally use environment variables for parameterizing their
  runtime configurations
- Kubernetes provides a way of managing more complex configuration files using a
  simple resource called ConfigMaps
- ConfigMaps can be created using directories, files or literal values using
  following CLI command:

```bash
$ kubectl create configmap <map-name> <data-source>
# map-name: name of the config map
# data-source: directory, file or literal value
```

## Credentials Management: Secrets

- Similar to ConfigMaps, Kubernetes provides another valuable resource called
  Secrets for managing sensitive information such as passwords, OAuth tokens,
  and ssh keys.
- A secret can be created for managing basic auth credentials using the
  following way:

```bash
# write credentials to two files
$ echo -n 'admin' > ./username.txt
$ echo -n '1f2d1e2e67df' > ./password.txt
# create a secret
$ kubectl create secret generic app-credentials --from-file=./
username.txt --from-file=./password.txt
```

### Credentials From Environment Variables

```bash
$ export DATABASE_URI='postgres://admin:s3cr3t@postgres:5432/postgres'
$ kubectl create secret generic db-creds --from-literal=databaseuri=$DATABASE_URI
```

Creates the following

```yaml
apiVersion: v1
kind: Secret
data:
  database-uri: cG9zdGdyZXM6Ly9hZG1pbjpzM2NyM3RAcG9zdGdyZXM6NTQzMi9wb3N0Z3Jlcw==
```

### Create Secrets from Literals

```bash
kubectl create secret generic dev-db-secret \
 --from-literal=username=devuser \
 --from-literal=password='s3cr3t' \
 --dry-run=client -o yaml
```

Output from create command:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: dev-db-secret
type: Opaque
data:
  username: ZGV2dXNlcgo=
  password: czNjcjN0Cg==
```

### Secret Yaml Example

```yaml
apiVersion: v1
  kind: Secret
  metadata:
    name: ecommerce-apikey
    namespace: default
  data:
    secret: <place base64 encoded secret here>
```

### Using Secrets

```yaml
apiVersion: apps/v1
kind: Deployment
---
spec:
  containers:
    - name: pet-demo
      image: pet-demo:v1
      imagePullPolicy: IfNotPresent
      ports:
        - containerPort: 5000
          protocol: TCP
      env:
        - name: DATABASE_URI
          valueFrom:
            secretKeyRef:
              name: pet-creds
              key: binding
```

## Kubernetes Rolling Updates (Zero Downtime Deployments)

```bash
$ kubectl set image deployment/<application-name> <container-name>=<container-image-name>:<new-version>
```

## Kubernetes Autoscaling

Kubernetes allows pods to be manually scaled either using ReplicaSets or
Deployments. This can be achieved using the following CLI command:

```bash
$ kubectl scale --replicas=<desired-instance-count> deployment/<application-name>
```
