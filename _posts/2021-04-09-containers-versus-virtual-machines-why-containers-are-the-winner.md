---
layout: post
title: "Containers versus Virtual Machines: Why Containers are The Winner"
date:   2021-04-09 20:47:52 +0100
---

## Introduction

Welcome to Module 3 of Lesson 1. This is an in-depth insight into Containers versus Virtual Machine. The module plays an important role in your understanding of [Application Modernization and Containers](https://docs.microsoft.com/en-gb/documentation/). I design this course and I have applied some of my knowledge and expertise in the arena of Microsoft\'s [Azure Kubernetes Service](https://mohamedradwan-devops.github.io/posts/azure-kubernetes-service-aks-deep-dive-free-course/) (AKS). https://youtu.be/5hEHQfMFGrI First, let\'s take a look at what exactly is a Virtual Machine.

## What is a Virtual Machine (VM)?

A virtual machine is just like your personal computer, minus the physical parts. The machine is a software copy that contains a Virtual Processor, Memory, Storage, and Networking resources. VMs can host an operating system, but Containers cannot. Virtual machines are an ideal option when: 

- You wish to have total control of the OS.
- Want to run custom software.
- Want to run custom hosting configurations.

Think of a VM as a computer that can run Windows as well as Linux, depending on the user preference.

![Virtual Machine AKS](/assets/img/2020/10/Virtual-Machine-AKS.png)

## Challenges of VM (Virtual Machine)

Virtual machines have the ability to host hundreds to thousands of workloads. The challenge with VMs is is that they are resource consumers. Imagine your personal computer [running Windows](https://docs.microsoft.com/en-gb/documentation/) or Mac, and the resources it requires to boot up and stay functional. Now multiply this by the hundreds and thousands. Another challenge is how can you transfer the machines from one place to another? Again imagine you wish to transfer 100gb of your personal content, over the internet, to another machine. How fast will the process be? When it comes to a professional set up, apps will need to be transferred between a testing environment, pre-production, and production. This is where containers make their mark.

![Hosting workloads in virtual machine AKS](/assets/img/2020/10/Hosting-workloads-in-virtual-machine-AKS.png)
## Advantage of Containers

Containers are a great solution to solve the challenges posed by VMs. Imagine you wish to ship a package to a particular destination in the world. Once you place the package in a container, you can send it to just about anywhere: Asia, Africa, even Australia. Software Containers work in a similar way. You can package an app, place it inside a container, then send it to any destination you choose - A personal machine, a colleague\'s machine, a test environment, or [even the cloud](https://mohamedradwan-devops.github.io/2020/06/16/announcing-cloud-devops-visions-community/).

![Advantages of using a container over a VM](/assets/img/2020/10/Advantages-of-using-a-container-over-a-VM.png)

## 3 Key Benefits of Containers

Compared to VMs, Containers offer key benefits to the user. We present the three main advantages:

- Enables the app to run efficiently across different computing environments.
- Holds everything essential to an app - from code to system tools to settings.
- Multiple containers are managed by a single OS, making them more lightweight than VMs.

![Container vs VM Virtual Machine](/assets/img/2020/10/Container-vs-VM-Virtual-Machine.png)

## Summary

Here\'s a quick snapshot of how VMs compare against Containers: Containers carry a [distinct advantage](https://docs.microsoft.com/en-gb/documentation/): They are lightweight, flexible, runs on diverse environments, and most importantly, uses a secured and isolated host. Consider this statistic: Containers are expected to grow from a \$2.1 billion industry to \$4.3 billion in 2022. Virtual machines have served us well in the past. The future, however, seems to firmly belong to Containers.
