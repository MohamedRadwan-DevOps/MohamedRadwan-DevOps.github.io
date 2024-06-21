---
layout: post
title: "Deploying infrastructure automatically to the cloud using Terraform and Azure pipelines Tutorial"
date:   2020-01-10 13:08:48 +0100
---

The following video has all the steps on how to do this tutorial:  

{% include embed/youtube.html id='KiCZzJlS16A' %}

## Intro

In this post, you are going to see a complete tutorial on how to use [Terraform](https://www.terraform.io/) for automating infrastructure as code to the cloud and using [Azure pipeline](https://azure.microsoft.com/en-gb/services/devops/pipelines/)We will see and learn different DevOps and infrastructure components and configurations.

## Run and execute Continuous Integration (CI) pipeline

So, first, I will open Azure pipeline then start navigating to the continuous integration pipeline and queue a build. This pipeline will run a build for a web application developed in ASP.NET. It will first start by restoring all the NuGet packages, building the application, running unit tests, and then creating the web package.zip file for the web application. After that, the pipeline will store the web package on Azure DevOps artifacts. Also, the pipeline will store the Terraform configuration file .tf on the artifact along with the web package.zip.  
[![Terraform workflow](/assets/img2020/01/Terraform.gif)](https://mohamedradwan-devops.github.io/posts/deploying-infrastructure-automatically-to-the-cloud-using-terraform-and-azure-pipelines-tutorial/terraform/)

## Understanding Terraform configuration file and language

So, first, what is the Terraform configuration file? Terraform configuration file is the infrastructure as code. It uses its own language known as Hashicorp Configuration Language (HCL), or optionally JSON. HCL is very similar to YAML. This file describes to the Terraform engine the needed infrastructure for our application.

> For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**
{: .prompt-tip }

## How does Terraform work?

Before digging more into the Terraform configuration file, let's first understand how Terraform works. Terraform generates or compiles the configuration file into an execution plan, which describes what it will do in order to reach the desired state for the needed infrastructure for the application. After that, Terraform executes this plan to build the described infrastructure, which is explained in the configuration file and after that, Terraform stores the infrastructure state in a state file in a storage area. When the configuration changes, Terraform is able to understand all the changes, and not just create a new execution plan but instead, it creates an incremental execution plan which can be applied.

## Storing Terraform state file

By default, Terraform stores state locally in a file named terraform.tfstate. When working with Terraform in a team, using a local file makes Terraform very complicated, which is why it's better to work with a remote storage area. As I have now, the web package and the Terraform configuration file .tf file on Azure DevOps artifacts.

## Run and execute Continuous Deployment (CD) pipeline

The next step is to run a continuous deployment pipeline (CD). The first step in the continuous deployment pipeline is to create the resource group, then the storage account needed to store the Terraform state. Once the storage account is created, the pipeline will get the storage key so it can be used later by the pipeline to save the Terraform.tfstate file to that storage account.

## Installing Terraform on the pipeline agent

After that, the pipeline will pick up the Terraform configuration file and then start installing Terraform on the pipeline agent machine. Once the pipeline looks at the Terraform configuration file, it will understand that this configuration file is targeting the Azure cloud provider. Then the initiate command will start installing the Azure suite which is required for Terraform to interact with the Azure cloud provider.

## Generate Terraform execution plan and apply it

Once this is complete, the plan command will be executed which transforms or generates or compiles the Terraform configuration file into an execution plan that describes the complete infrastructure and its desired state. After that, the apply command for the execution plan will be executed which will start creating the infrastructure and its desired state. It will start by creating an Azure service plan and Azure web app. After creating the infrastructure is done, Terraform will start storing the infrastructure state in the storage account. If there is any change in the configuration, Terraform doesn't generate a new execution plan. Instead, it generates an incremental execution plan which can be applied.

## Deploy the application package to the web app

Now the infrastructure is ready. The pipeline will pick up the web package.zip file and start deploying that to the web app and extracting all package files to the web app. Now my web app is ready, so I can browse and open this web app from the cloud.
