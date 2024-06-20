---
layout: post
title: "Docker For Beginners Step-by-Step Tutorial"
date: 2019-05-31 14:47:56 +0100
---

In this post and video, you will learn how to work with Docker and containers. This includes understanding the differences between VM, Containers, and Hyper-V Containers. The tutorial covers:

- What is [Docker](https://www.docker.com/) and its value proposition compared to VM and Containers.
- How to install and uninstall Docker on [Linux](https://www.linux.org/) and Windows.
- The difference between Images and Containers.
- Container Deployment Workflow and container registry.
- Dockerfile basics.
- Enabling Bridge Networking and Port Mapping in Docker images.
- The relation between Containers, CI/CD, and DevOps.

Watch the full tutorial video here: [Docker For Beginners Step-by-Step Tutorial](https://www.youtube.com/watch?v=3RJv6yVfaRE)

---

### Overview

In this post and video, you are going to get an overview of container concepts and how to install Docker, uninstall it, and perform various Docker-related tasks. 

### Commands Used in the Tutorial

Here are the commands used during the demo, making it easy for you to copy and paste them:

- `docker`
- `apt install docker.io`
- `sudo bash`
- `exit`
- `sudo nano /etc/apt/sources.list`
- `sudo apt update`
- `sudo apt install docker.io`
- `sudo apt remove docker.io`
- `sudo docker pull nginx`
- `sudo docker images`
- `sudo docker ps`
- `sudo docker run nginx`
- `sudo docker stop yourContainerID`
- `sudo docker pull tutum/hello-world`
- `sudo docker run -p 8080:80 tutum/hello-world`

### Key Concepts

1. **Virtual Machines vs. Containers vs. Hyper-V Containers**:
   - Virtual machines are created and managed by hypervisors, such as VirtualBox, Hyper-V, or VMware, running on a host operating system that could be different from the guest OS. VMs offer high-level isolation but are resource-intensive and less portable.
   - Containers leverage the existing operating system to offer separation without the overhead of duplicating the OS. They require lower RAM, are easier to move over networks, and are cost-effective.

2. **Docker Overview**:
   - Docker provides an efficient way to run applications in isolated environments (containers) using the host OS kernel. This eliminates the need for a separate OS for each application, reducing resource usage and improving portability.

3. **Dockerfile and Port Mapping**:
   - A Dockerfile allows you to automate the creation of Docker images using scripts.
   - Port mapping enables you to expose ports from the container to the host machine.

4. **Containers and CI/CD**:
   - Containers play a crucial role in Continuous Integration and Continuous Deployment (CI/CD) pipelines by providing consistent environments for development, testing, and production.

### Demo

The demo includes steps for installing Docker, uninstalling it, updating packages, editing the package source file, running containers, downloading images, and more.

For detailed commands and step-by-step instructions, refer to the tutorial video: [Docker For Beginners Step-by-Step Tutorial](https://www.youtube.com/watch?v=3RJv6yVfaRE)

---

### Tip: Kubernetes for Beginners

For more information about working with Kubernetes clusters and deploying them to **Azure Kubernetes Service (AKS)**, see **[Kubernetes cluster for beginners](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**

---

You can find more information about DevOps in the following post: [Building and Deploying Your Code with Azure Pipelines](https://mohamedradwan-devops.github.io/posts/building-and-deploying-your-code-with-azure-pipelines/)
