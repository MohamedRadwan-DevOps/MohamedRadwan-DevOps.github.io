---
layout: post
title: "Containers - The Perfect Solution For Running Microservices"
date: 2018-04-17 11:39:27 +0100
---

## Introduction

A container image is a lightweight executable package of a piece of software that will always run the same, regardless of the environment you are using it with. The series of videos presented below will explain the basic and advanced principles of using Containers, as well as various technologies and services around it.

>If you would like to learn more about enhancing frontend development code quality, it includes understanding different types of JavaScript unit testing frameworks like Jasmine, Mocha, Jest, different types of task runner like Grunt and Gulp, different types of linting tools, like JSHint, ESLint, JSLint, CSSLint, different types of code formatter like Prettier and Tidy, how to write your first JavaScript using test with Jasmine standalone version, how to run JavaScript unit tests using Grunt.
Command Line and PhantomJS, how to calculate code coverage for JavaScript unit tests using Istanbul, how to run JavaScript unit tests using Visual Studio Test Explorer using chutzpah extension, how to lint JavaScript code using JSHint and how to run that from Command Line using Grunt, finally it shows how to integrate all the quality practices with Visual Studio Team Service Build automation so it can be part of CI/CD or Continuous Integration and Continuous Delivery, - have a look at the [this post](https://mohamedradwan-devops.github.io/posts/front-end-code-quality-javascript-unit-test-and-linting-automation-with-vsts-build/)
{: .prompt-tip }

## Containers Introduction and abstract

In this video series, we will understand what is the story behind containers and what drives or the needs for it, we will know why companies moved from traditional solution architecture to Microservices and how this put containers as the perfect solution for running them, we will get a quick intro to clear some definitions, tools, and keywords related to this ecosystem, for example. We will understand what is the difference between VM, Container and Hyper-V Container, why we would prefer container over VM and when the VM is better. We will understand the difference between container and image and know the life cycle of creating a new image and why I do that, like adding more layers to the base image, push that to container images registry on the cloud. Then pull that from the registry to anywhere to have a new container. And we will understand different technologies and services around the container, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), Azure Container Registry, etc. We will see how to create a Linux machine on Azure, remote connect to it using Git bash and PuTTY, how to install Docker, display all the images that exist on the machine, pull new image from Docker Hub, run and stop a container, display running containers and many others, we will see also the same steps on Windows with Docker. 

{% include embed/youtube.html id='X13AdWYC2KI' %}

## 1. Microservices and Containers what and why? {#_Toc511735171}

This is the first video in this series. We will understand what is the story behind containers and what drives or the needs it. We will know why companies moved from traditional solution architecture to Microservices and how this put containers as the perfect solution for running them. We will get a quick intro to clear some definitions, tools, and keywords related to this ecosystem. For example, we will understand what is the difference between VM, Container and Hyper-V Container. Why we would prefer container over VM and when the VM is better, we will understand the difference between container and image and know the life cycle of creating a new image and why I do that, like adding more layers to the base image, push that to container images registry on the cloud, then pull that from the registry to anywhere to have a new container. We will understand how the orchestration and clustering work for containers by managing the underlying nodes which host the containers. We will understand different technologies and services around the container, like Docker, Docker Hub, Docker Swarm, Kubernetes, Azure Container Services (AKS), Azure Container Registry.

{% include embed/youtube.html id='18i94MfJSAI' %}

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/). The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management, and, moreover, how to configure an end-to-end pipeline for deploying applications on Azure.
{: .prompt-info}

## 2. Creating Linux VM on Azure and establish a remote connection

In this video, we will see how to create a Linux machine on Azure, we will select Ubuntu server and remote connect to it using Git bash and PuTTY, and we will see how to test that our connection is established using the sudo command.

{% include embed/youtube.html id='C0ecnvmdAuQ' %}

## 3. Working with Docker on Linux 

In this video, we will start working with container using Docker, so first we will get more familiar with some Linux commands like sudo and sudo bash, understanding the difference between apt-get and Yum, installing and uninstalling Docker, pull images from Docker-Hub, run a container with "docker run", list all the running containers in the machine by "docker ps", see all the containers from the host machine using process tree or pstree and many others.

{% include embed/youtube.html id='lZIzkOLbBoI' %}


>You can see this video, if you would like to find more information about a walkthrough introducing the Release Management and Build Automation using TFS 2017/2015. Step by step about all process, starting from creating the project, check in the code in the source control, create a build definition and trigger the build, and also create a release pipeline. Learn how to configure properly the build steps, including Copy Files and Publish Build Artifacts. See how to create a new release definition, add environments and link to build definition. Afterwards see how to add tasks to the release definition, like Windows Machine File Copy and configure it properly.
{: .prompt-tip }
{% include embed/youtube.html id='vev3Czaa1pA' %}

## 4. Creating Windows VM on Azure and working with Docker {#_Toc511735174}

In this video, we will see how to create a Windows virtual machine on Azure, I will use Windows 10 machine, connect remotely to it using remote desktop, installing Docker for windows in Linux mode, we will see how to verify that Docker installation succeeded and fix some errors, we will also pull docker hello-world image from Docker-Hub and running a container from it and also pull a SQL Express image as well as nginx, we will also run many containers from the same images and see how we can verify that and many others.

{% include embed/youtube.html id='W9ImzKuQGQ8' %}


## The commands that are in the Linux video:

```
$ sudo Clean screen
$ Reset or clear
Type docker without sudo and without installing docker
$ docker
Install docker
$ sudo apt-get update && sudo apt-get install -y docker.io
Now type docker again
$ docker
List all images of docker
$ docker images
"Got permission denied", now we understand we need to use sudo with every command as we don't have permission without sudo, so let's list all images of docker using sudo
List all images of docker
$ sudo docker images
Type sudo bash so we don't need to type sudo with each command
$ sudo bash

## Type exit to exit from the root user
# exit

sudo allows users to run programs with the security privileges of another user (normally the superuser, or root). bash starts a new bash shell. So, sudo bash starts a new bash shell with the security privilege of root user.
Run hello world image to know we are working correctly
$ sudo docker run hello-world
Uninstall docker then install docker again
$ sudo apt-get remove docker docker-engine docker.io
Try to see docker help
$ sudo docker run --help
Type docker ps (process) to see all running images (no images running)
$ sudo docker ps
Go to Docker hub https://hub.docker.com/explore/
Select nginx image and see the pull command
Pull this image from Docker hub
$ sudo docker pull nginx
List docker images
$ sudo docker images
Run the container of nginx image
$ sudo docker run nginx
From another PuTTy see Docker process, you should see now nginx container is running
$ sudo docker ps
On the root, access the process tree, you should see the running container and what is inside
$ sudo pstree
Stop the container by type docker stop and give the container ID which you can get from docker images
$ sudo docker stop ee3434341
```

## The commands that are in the Windows video:

```
Type docker ps (process) to see all running images
docker ps
Go to Docker hub https://hub.docker.com/explore/
Select nginx image and see the pull command
Pull this image from Docker hub
docker pull nginx
List docker images
docker images
Run the container of nginx image
docker run nginx
see now nginx container is running
docker ps
```
