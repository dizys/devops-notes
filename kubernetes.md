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

## Kubernetes is an Orchestration Platform

- Scheduling: decide where containers run
- Lifecycle and Health: keep containers running and restart them if they fail
- Scaling: grow and shrink deployments as needed
- Naming and Discovery: help containers find each other
- LoadBalancing: distribute traffic across containers ...and a whole lot more

## Why Do You Need Container Orchestration?

- Deploy applications to servers without worrying about specific servers
- Scale the application horizontally up and dow
- This is called container auto-healing or Restore the application if the server
  on which it worked fails rescheduling

## Kubernetes has a Declarative API

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

## Kubernetes All-In-One

- You can run Kubernetes all in one VM for development work (not for
  production!)
- MiniKube is great for setting this up
- MiniShift will deploy a development version of RedHat OpenShift 3.x which uses
  Kubernetes
- CRC (Code Ready Container) will deploy OpenShift 4.x

## Kubernetes is the new "Cloud OS"

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

## Types of Services

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

## Use Case for Multiple Containers in a Pod

Pods can be used to host vertically integrated application stacks (e.g. LAMP),
but their primary motivation is to support co-located, co-managed helper
programs, such as:

- Content management systems, file and data loaders, local cache managers, etc.
- Log and checkpoint backup, compression, rotation, snapshotting, etc.
- Data change watchers, log tailers, logging and monitoring adapters, event
  publishers, etc.
- Proxies, bridges, and adapters
- Controllers, managers, configurators, and updaters
