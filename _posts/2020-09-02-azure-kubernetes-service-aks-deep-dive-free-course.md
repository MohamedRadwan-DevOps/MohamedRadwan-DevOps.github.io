---
layout: post
title: "Azure Kubernetes Service (AKS) Deep Dive Free Course"
date: 2020-09-02 21:21:06 +0100
pin: true
---

- [Introduction](#_Toc49940611)
- [Course Structure, Modules, and Overview](#_Toc49940612)
- [Module 1: Introduction to Application Modernization and Containers](#_Toc49940613)
- [Module 2: Understanding and working with Docker](#_Toc49940614)
- [Module 3: Working with Containerized Applications in Azure](#_Toc49940615)
- [Module 4: Networking, Scaling, Helm and Advanced Deployment in AKS](#_Toc49940616)
- [Module 5: Kubernetes Security, Governance, Monitoring and Logging](#_Toc49940617)
- [References and Resources](#_Toc49940618)
- [Summary](#_Toc49940619)

## Introduction {#_Toc49940611}

I am pleased to announce my new free course **Azure Kubernetes Service (AKS) Deep Dive**. This course will provide a complete roadmap for Docker, Kubernetes, and Azure Kubernetes Service (AKS) for those people who want to start their journey to containerized applications in Azure, cloud, and get a real deep dive with hands-on. This course is built from the ground up, so it can be used by very beginners as well as advanced level learners. It has several modules, lessons, and demos that cover the entire course, moving from the very basic to very advanced topics with deep hands-on labs and demos. The course is structured to make it very easy to navigate between modules, lessons, and demos as well as easily finding any video inside the course. This course is available in two languages, English & Arabic.

**English YouTube channel**: [YouTube Link](https://www.youtube.com/watch?v=EAA9x1kz674&list=PLe14MLC-Nwy74dECq18Y5SPzrUK9ri47L)

**Arabic YouTube channel**: [YouTube Link](https://www.youtube.com/watch?v=ZYXkJusl8mw&list=PL68G6wbDBVgjKLGOyGwnxcdYQlFiGQdh7)

## Course Structure, Modules, and Overview {#_Toc49940612}

**Azure Kubernetes Service (AKS) Deep Dive** course is divided in 5 modules, each of them divided into lessons and demos. So, there are 37 lessons and 33 demos in total of 70 videos.

- Module 1: Introduction to Application Modernization and Containers
- Module 2: Understanding and working with Docker
- Module 3: Working with Containerized Applications in Azure
- Module 4: Networking, Scaling, Helm and Advanced Deployment in AKS
- Module 5: Kubernetes Security, Governance, Monitoring and Logging

Let's see in detail what are the lessons and demos in each module and what you can expect to see and learn in each module.

## Module 1: Introduction to Application Modernization and Containers {#_Toc49940613}

This module consists of 4 lessons as the following:

1. Introduction and Course Overview - explanation about everything you need to know about this course, its scope, modules, lessons etc.
2. Understanding application modernization - understand what modernization of an application actually means, as well as some tips for the process of modernizing an application and its importance
3. Container vs. Virtual Machine - an introduction to Containers and Virtual Machines, and an explanation of why we might need to work with Containers over Virtual Machines
4. Introduction to Kubernetes and containers orchestration - an overview of Kubernetes and an explanation of why we may need to work with container orchestration

## Module 2: Understanding and working with Docker {#_Toc49940614}

This module consists of 9 lessons and 10 demos as the following:

1. Introduction and Module Overview - quick introduction about the module and what to expect to learn in detail for the module
2. Getting started with Docker - overview and introduction about Docker
3. Working with Docker containers - more information about how to work with Docker using several commands
    - Demo: Working with Docker container on Linux - learn practically how to work with Docker container on Linux
    - Demo: Working with Docker container on Windows - see the difference between working with Docker on Linux and Windows machines
    - Demo: Doing several actions using Docker commands - practical presentation of several actions with Docker commands
4. Understanding Docker file and image layers - how the Docker file is working and how it is divided into layers
    - Demo: Working with Docker file - how you can execute the Docker command and build an image
    - Demo: Executing Docker container and image workflow - how the Docker workflow is working as well as mapping the workflow into interactive commands
5. Working with Docker Volumes - how Docker can interact with volumes
    - Demo: Using Docker Volumes - working with volumes in Docker
6. Understanding Networking in Docker - networking containers through the use of network drivers
    - Demo: Working with networking in Docker - how to work with networking inside a Docker container
7. Working with Docker compose - what is Docker compose, how to work with Docker compose and why we need it
    - Demo: Working with Docker compose - how to work with Docker compose
8. Understanding multi-stage build - what is the reason behind using a multi-stage build
    - Demo: Working with multi-stage build - how to work with multi-stage build
9. How to build and run unit testing inside Docker container - details about building and running unit tests inside a Docker container
    - Demo: Running unit testing inside Docker container - how to run unit tests inside a Docker container

## Module 3: Working with Containerized Applications in Azure {#_Toc49940615}

This module has 8 lessons and 5 demos as the following:

1. Introduction and Module Overview - understand in detail what to expect to learn and see in each lesson in this module
2. Azure Container Registry (ACR) - an overview about Azure Container Registry, how to provision and how to work with ACR
    - Demo: Working with Azure Container Registry (ACR) - practical presentation of working with ACR using several commands
3. Kubernetes Architecture and Components - first detailed lesson in which the Kubernetes architecture (AKS or non-AKS) is explained, focusing on the details of the architecture of Kubernetes and how it is related to AKS
4. Kubernetes Resources and Objects - more details about the structure of Kubernetes and what the different components that construct Kubernetes are
5. Interacting with Kubernetes (Kubectl and Dashboard) - how to interact with Kubernetes API using the Kubectl command-line tool or using the dashboard from the web and the UI
    - Demo: Working with Kubectl CLI - practical presentation of using a Kubectl as a command line to interact with Kubernetes using several commands
    - Demo: Working with Kubernetes Dashboard - how to do several interactions using Kubernetes Dashboard
    - Demo: Working with Kubernetes manifest multi-container pod - practical presentation of Kubernetes manifest multi-container pod
6. Managing and upgrading Azure Kubernetes Service (AKS) cluster - understand what and how to upgrade an AKS cluster
    - Demo: Upgrading Azure Kubernetes Service (AKS) cluster - learn how to upgrade an AKS cluster step by step
7. Containerization security in Azure - detailed explanation of security for AKS in Azure as a fundamental security
8. Introduction to OAM and dapr - detailed overview about OAM and dapr

## Module 4: Networking, Scaling, Helm and Advanced Deployment in AKS {#_Toc49940616}

This module consists of 10 lessons and 12 demos as the following:

1. Introduction and Module Overview - understand in detail what to expect to learn and see in each lesson in this module
2. Basic networking in Azure Kubernetes Service (AKS) - introduction to how to use basic networking in AKS
    - Demo: Working with basic networking in AKS - practical presentation of basic networking in AKS
3. Advanced Networking in Azure Kubernetes Service (AKS) - advanced level of networking in AKS
    - Demo: Advanced networking with Azure Container Network Interface (CNI) in AKS - how to do advanced networking in AKS and how to use Azure Container Network Interface in AKS
    - Demo: Configuring network for AKS using Kubernetes - how to configure network for AKS using Kubernetes
4. Understanding scaling applications in AKS - focus on the scaling in AKS for both auto-scaling and manual scaling
    - Demo: Scaling application in Azure Kubernetes Service (AKS) - how to scale an application in AKS
5. Configuring application in AKS for High Availability - how to achieve high availability in AKS
    - Demo: Working with Azure Kubernetes Service (AKS) for High Availability - explanation of how to implement high availability for AKS
    - Demo: Backup and restore - how to do backup and restore in AKS
    - Demo: Deploy application across Availability Zones - practical presentation on how to deploy an application across Availability Zones
    - Demo: Multi-Region AKS cluster - demo about Multi-Region AKS cluster
6. Configuring data volumes in AKS using Azure Disks - using the volumes inside or within AKS using the Azure Disks
    - Demo: Creating volumes with Azure Disks in AKS - how to create volumes and work with Azure Disks in AKS
7. How to deploy and provision AKS with Terraform - explanation of the infrastructure using Terraform and how to provision AKS using Terraform
    - Demo: Deploying and provisioning AKS with Terraform - practical presentation of how to deploy and provision AKS using Terraform
8. How to Deploy application to AKS using CI/CD with Azure Pipeline - detailed end-to-end explanation of how to build and deploy the application to AKS using Azure Pipeline
    - Demo: Deploying application to AKS using CI/CD with Azure Pipeline - presentation of the entire process of deploying an application to AKS with Azure Pipeline
9. Using Helm for Release Management to AKS - details about Helm, what it is, how and why we use it
    - Demo: Working with Helm for Release Management to AKS - practical presentation for Helm
10. Advanced topics for managing AKS - several advanced topics for AKS that you should be aware of

## Module 5: Kubernetes Security, Governance, Monitoring and Logging {#_Toc49940617}

This module consists of 7 lessons and 6 demos as the following:

1. Introduction and Module Overview - understand in detail what to expect to learn and see in each lesson in this module
2. Securing data running on Azure Kubernetes Service (AKS) - detailed explanation about security for AKS
    - Demo: Using Service Principal and Managed Identity in AKS - how to use Service Principal and Managed Identity in AKS
    - Demo: Securing network traffic and cluster configuration file - how to secure network traffic and cluster configuration file
3. Integrating Azure Active Directory with AKS and manage access using RBAC - integration between Azure Active Directory and how to integrate the Role-Based Access Control with AKS
    - Demo: Integrating Azure Active Directory with AKS - practical presentation of the integration of Azure Active Directory with AKS
4. Integrating Azure Kubernetes Service (AKS) with Azure Security Center - the importance of the integration between AKS and Azure Security Center
5. Introduction to Monitoring and logging for containerized applications - explanation of Monitoring and logging for containerized applications
6. Monitoring and logging containerized applications using Application Insights, Log Analytics, and Azure Monitor - how to monitor and log using Application Insights, Log Analytics, and Azure Monitor
    - Demo: Monitoring containers using Azure Monitor - practical presentation of monitoring containers using Azure Monitor
7. Getting started to Monitor AKS with Continuous Optimization Cloud (CCO) Dashboard - introduction to Monitor AKS using CCO Dashboard
    - Demo: Monitoring AKS using Continuous Optimization Cloud (CCO) Dashboard - practical presentation of monitoring AKS using CCO Dashboard
    - Demo: Monitoring using Azure Monitor and Grafana - how to monitor using Azure Monitor and Grafana

## References and Resources {#_Toc49940618}

This course is developed and designed using several references, the main of them as the following:

- [Microsoft Learn](https://docs.microsoft.com/en-us/learn/)
- [Microsoft Ignite the tour resources](https://techcommunity.microsoft.com/t5/microsoft-ignite-the-tour/ct-p/MicrosoftIgniteTour)
- [Microsoft docs](https://docs.microsoft.com/en-us/azure/)

Also, more resources could be found on this blog or my YouTube channel:

- [YouTube Channel](https://www.youtube.com/user/MRadwanMSF/)

## Summary {#_Toc49940619}

Azure Kubernetes Service (AKS) Deep Dive is a free course that I am developing from my real experience. It will provide a complete roadmap for Docker, Kubernetes, and AKS for those people who want to start their journey to containerized applications in Azure, cloud, and get a real deep dive with hands-on. This course is built from the ground up, so it can be used by very beginners as well as advanced level learners. It has several modules, lessons, and demos that cover the entire course, moving from the very basic to very advanced topics with deep hands-on labs and demos. This course is available in two languages, English & Arabic.
