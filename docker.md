---
description: Introduction to Docker
---

# Docker

## Docker Concepts

- Docker is a platform for developers and sysadmins to develop, deploy, and run
  applications with containers
- The use of Linux containers to deploy applications is called containerization
- Containers are not new, but Docker make their use for easily deploying
  applications simple

## Benefits of Containers

- Great isolation
- Great manageability
- Container encapsulates implementation technology
- Efficient resource utilization
- Fast deployment

### Containers Enable Immutable Delivery

Build once... run anywhere

- The same binary that a developer runs on their laptop, runs in production
- All dependencies are package in the container
- Facilitates rolling updates with immediate roll-back
- Consistency limits side-effects

## Containers are just Linux Capabilities Under the Covers

Containers are:

Linux® processes with isolation and resource confinement that enable you to run
sandboxed applications on a shared host kernel using cgroups, namespaces, and
chroot.

- **cgroups**: Control Groups allow you to control how much resources are
  allocated to a process (e.g., memory, cpu. etc.)
- **namespaces**: Control access to what you can see (e.g., processes, mounts,
  networking, etc.). What you can't see, you can't access!
- **chroot**: Allows you to change the root filesystem. This allows the apparent
  root to be any linux filesystem whether it be ubuntu, opensuse, redhat or
  otherwise (i.e., overlay filesystem)

In other words, Docker Containers allow you to control:

- What resources a process can see
- What resources a process can control
- What filesystem a process uses

## Containers and Virtual Machines

A container runs natively on Linux and shares the kernel of the host machine
with other containers It runs a discrete process, taking no more memory than any
other executable, making it lightweight

By contrast, a virtual machine (VM) runs a full-blown “guest” operating system
with virtual access to host resources through a hypervisor . In general, VMs
provide an environment with more resources than most applications need

To summarize, Virtual Machines are heavy-weight emulations of real hardware.
Containers are light-weight process The app looks like it’s running on the Host
OS.

## Containers are:

- **Flexible**: Even the most complex applications can be containerized
- **Lightweight**: Containers leverage and share the host kernel
- **Interchangeable**: You can deploy updates and upgrades on-the-fly
- **Portable**: You can build locally, deploy to the cloud, and run anywhere
- **Scalable**: You can increase and automatically distribute container replicas

### Containers are Scaled on Demand

- Cloud Native Microservices use redundancy for resiliency
- Containers are spun up as needed and destroyed when no longer needed
- This why containers should be immutable and stateless

### Docker Provides Portable Isolated Environments

- Docker gives you portable isolated environments
- You could have an application that requires Python 3.6 running in one
  container
- With an application that requires Python 2.7 running in another
- Completely isolated from each other will no chance of library collisions

## Images and containers

A container is launched by running an image. An image is an executable package
that includes everything needed to run an application--the code, a runtime,
libraries, environment variables, and configuration files. A container is a
runtime instance of an image i.e., what the image becomes in memory when
executed (that is, an image with state, or a user process). You can see a list
of your running containers with the command, `docker ps`, just as you would in
Linux

### Docker Layered Filesystem

- Docker uses a Copy-On-Write layered filesystem. You can see the layers when
  you pull or push an image
- Only changes from the read-only layers are copied

### Images and Layers

- Each Docker image references a list of read- only layers that represent
  filesystem differences
- Layers are stacked on top of each other to form a base for a container’s root
  filesystem
- When you create a new container, you add a new, thin, writable layer on top of
  the underlying stack
- All changes made to the running container - such as writing new files,
  modifying existing files, and deleting files - are written to this thin
  writable container layer

## Docker Volumes

- Volumes are easier to back up or migrate than bind mounts.
- You can manage volumes using Docker CLI commands or the Docker API.
- Volumes work on both Linux and Windows containers.
- Volumes can be more safely shared among multiple containers.
- Volume drivers let you store volumes on remote hosts or cloud providers, to
  encrypt the contents of volumes, or to add other functionality.
- New volumes can have their content pre-populated by a container

## Containers should be...

- **Stateless**: All state should be maintained in a Database, Object Store, or
  Persistent Volume

- **Light Weight**: Only one process per container i.e., Container dies when
  process dies
- **Immutable**: Do not install an ssh daemon or any other means of entering the
  container!
- **Run from Docker Registry Images or Built from Dockerfiles**: Treated like
  code, versioned, and reconstituted when needed... not built by hand!

### What do we mean by Stateless?

When we say STATE what do we mean?

- Any pieces of data about the client or transaction
- Could be the state of a session with the end-user
- These should be persisted somewhere (database, session cache, etc.) but NOT in
  memory!

## What Docker Is NOT?

Docker is NOT a Virtual Machine!

- Resist the temptation of putting a monolith in a container
- Resist the urge to run more than one process per container
- It’s a bad idea to store state in a container (just don’t do it!)

## What Can you Do with Docker?

- You can run **Containers** from the **Images** in the Docker Registry (e.g.,
  Docker Hub)
- You can build Docker **Images** that hold your applications and their
  dependancies
- You can create Docker **Containers** from those Docker images to run your
  applications
- You can share those Docker images via **Docker Hub** or your own Docker
  registry
- You can pull those images from the Docker registry to **deploy** them as
  Containers on a server running Docker Engine
- You can even deploy those containers in the **Bluemix** Container Cloud!

## Containers should be small

- Its a good practice to use a tiny Linux distribution for building containers
- Docker images should only contain the app and it’s required libraries (not a
  whole OS!)
- mall distributions have a small attack surface and are more secure
- Alpine is perfect for this base OS
