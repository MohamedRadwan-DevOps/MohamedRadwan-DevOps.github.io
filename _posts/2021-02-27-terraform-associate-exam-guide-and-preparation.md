---
layout: post
title: "Terraform Associate Exam Guide and Preparation"
date:   2021-02-27 20:16:53 +0100
---

## Agenda

The first is to explain where to ask questions and find resources for this initiative. So, there is a GitHub repo to store all resources, after that we will know and understand the exam objectives. Then we will understand an overview about an end-to-end demo after completing and covering all the exam objectives it\'s like a project at the end. The end-to-end demo should put much of what you have learned into a good example of a real 

![Terraform Associate Exam Preparation agenda](/assets/images/2021/02/Terraform-Associate-Exam-Preparation-agenda-1024x577.png)
## Exam Objectives

Understanding Infrastructure as Code (IaC) concepts. Understanding Terraform\'s purpose (vs other IaC). Understanding Terraform basics. Demonstrating that you can use the Terraform CLI (outside of core workflow). Demonstrating that you can interact with Terraform modules. Demonstrating that you can navigate the Terraform workflow. Demonstrating that you can implement and maintain a state. Demonstrating that you can read, generate, and modify Terraform configuration. Demonstrating that you understand Terraform Cloud and Enterprise capabilities.

## GitHub repo for the course

The following repo, I created on GitHub so you can just use it for this exam preparation activity, please click watch then click star to keep connected. If you have any questions or issues regarding the exam objectives or topics, please visit this repo ([click here](https://github.com/MohamedRadwan-DevOps/terraform-associate-exam-prep){target="_blank" rel="noopener noreferrer"}) and click issues then search for your question, if you couldn\'t find a similar one, please raise a new one.
<https://github.com/MohamedRadwan-DevOps/terraform-associate-exam-prep>
Also, make sure to review and follow the rules for asking questions or raising an issue because the issue must have a minimum quality of information.

![Terraform GitHub repo for Terraform Associate Exam Preparation](/assets/images/2021/02/Terraform-GitHub-repo-for-Terraform-Associate-Exam-Preparation-1024x573.png)

## Feedback and questions

Please go and provide me your feedback on YouTube about what you would like to see in the next session and what was good and what needs improvement. So, to summarize, if you have a question or inquiry use GitHub for feedback, use YouTube.

![Feedback on YouTube and questions on GitHub](/assets/images/2021/02/Feedback-on-YouTube-and-questions-on-GitHub-1024x572.png)

## The end-to-end demo for Terraform

The following is the end-to-end demo which including building a very small application web application and packaging the application building CI/CD pipelines and provision the environment on the cloud using the terraform.

![Terraform end-to-end-demo](/assets/images/2021/02/Terraform-end-to-end-demo-1024x575.png)

## Three days course to cover all the objectives

I divided the course into three sessions over three days. So, in each session or each day, I\'m going to cover three objectives of the exam.

![Terraform Associate Exam Preparation course and sessions](/assets/images/2021/02/Terraform-Associate-Exam-Preparation-course-and-sessions-1024x574.png)

## The problem with traditional infrastructure

So, let\'s look at the traditional infrastructure, if we get back to how we treat or how we\'re working with traditional infrastructure, you know usually you have a server or infrastructure and you just make some changes with your infrastructure again and again over years. This is the main problem that how we are going to replicate this server with all those changes?

![Challenges With Traditional Infrastructure](/assets/images/2021/02/Challenges-With-Traditional-Infrastructure-1024x571.png)

To replicate traditional infrastructure, the teams bring a lot of documents or a very huge document which explain what the process for the replication for that environment, we usually go through all the process and create the environment but it\'s not working because it is not the same, there is something is configured on the actual environment, but it is not known.

## Vicious circle of manual process

![Vicious Circle of manual process](/assets/images/2021/02/Vicious-Circle-of-manaual-process-1024x571.png)

This leads to a vicious circle of manual processes. So, let\'s understand how this happened? For example, if we look at the manual process it is usually well documented, so you can understand exactly what the steps are and then you start it starts taking a long time to implement this documentation, and then at the end, it has errors which make you add more verification in the document and the process which increase the process which ends up with more documentation taking more time more errors add verification, and this is what happened.

## Infrastructure workflow

This is a general workflow, so it starts with source control. So, you put all your infrastructure as code in the source control and once you want to make any changes, you just get the latest and just make the change, once you complete the change, you don\'t usually run the update or create or provision the infrastructure from your local machine, instead, the best practices usually is to push these changes to the remote repo and then run an automated build which will get the latest and start either creating or updating the environment.

![Infrastructure as code workflow with terraform](/assets/images/2021/02/Infrastructure-as-code-workflow-with-terraform-1024x572.png)

## Take-aways information

**Terraform Configuration file** You describe all the components or your entire datacentre or environment in terraform configuration file which has .tf extension.

**Resource Graph** Terraform builds a graph of all your resources and parallelizes the creation and modification of any non-dependent resources. because of this, Terraform builds infrastructure as efficiently as possible, and operators get insight into dependencies in their infrastructure.

**Providers** Terraform relies on plugins called "providers" to interact with remote systems. Terraform configurations must declare which providers they require so that Terraform can install and use them. Each provider adds a set of resource types and/or data sources that Terraform can manage.

**Configure a Provider** 

```hcl
provider "azurerm" {
  features {}
  version  = ">= 2.26"
}

provider_x_y {
  # example
  resource "azurerm_resource_group" "example" {
    # resource configuration
  }
}
```


**Control terraform version or other behaviours** 

```hcl
terraform {
  #...
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = ">= 2.26"
    }
  }
}
```

![Terraform provider control terraform block azurerm](/assets/images/2021/02/Terraform-provider-control-terraform-block-azurerm-1024x576.png)

## Continue in the video..
