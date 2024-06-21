---
layout: post
title: "Using Ansible To Automate Infrastructure on Azure Cloud Tutorial | Automating Infrastructure Deployments on Azure Using Ansible and Azure Pipelines"
date:   2020-01-08 17:04:08 +0100
---

The following video has all the steps on how to do this tutorial: 

{% include embed/youtube.html id='Q8aWeHCrGh4' %}

## Intro

This post will explain using Ansible to automate infrastructure deployment to Azure cloud using [Azure pipelines](https://azure.microsoft.com/en-gb/services/devops/pipelines/). In this post, we are going to see a complete tutorial for how to create infrastructure using infrastructure as code with Ansible and Azure pipeline.

## Create a Linux machine

So, I will start on my client machine. I have a Windows machine with Git bash installed. So, I can use Git bash as a terminal connection with SSH to the remote Linux machine. The next step is to start logging into my Azure portal and start creating a resource group and start creating a remote Linux machine. I need port 22 to be open so I can communicate with this machine using SSH. Once I complete the creation of the machine, I will log in to the machine from my local machine using SSH and the username and password I used to create the Linux virtual machine.  
![Ansible-Workflow](/assets/img2020/01/Ansible-Workflow.gif)

## Install and configure Ansible on the Linux machine

Then the first step is to start installing and configuring [Ansible](https://www.ansible.com/) on this machine. I will prepare this machine to be a remote Ansible machine. Part of that also is to install Azure SDK for Ansible and then test my virtual machine to make sure that Ansible is running correctly.

## Configure Authentication between Azure Pipelines and Ansible machine

After that, I will start configuring the authentication from the Ansible machine to my Azure subscription. I need to create a credential file inside the virtual machine. This virtual machine can have permission to my Azure subscription to create infrastructure for my application. After that, I will generate a pair of RSA keys, private and public key. Once this machine is ready, I will go to Azure DevOps and navigate to the project setting, then start using the private key to create a service connection. The main idea here is to make Azure pipeline have authentication to the virtual machine so it can communicate with it because Azure pipeline will execute Ansible playbook remotely on the Ansible virtual machine. This is because we are using Ansible to automate infrastructure.

> For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**
{: .prompt-tip }

## Run and execute Continuous Integration (CI) pipeline

Once I complete that, I will run a continuous integration build. Since this is a Java application, it will start the Maven task which will start doing all the tasks inside the POM or the Project Object Model which are restoring all the dependencies for the application, running all the unit tests, and so on. Then in the end, it creates the Java package which is a WAR file. After that, the pipeline stores the package on Azure DevOps artifacts so it can be ready for the CD continuous deployment pipeline to pick it up. Also, it will store the Ansible playbook.yml on the same artifacts so it can be ready to be picked up by the continuous deployment pipeline. We are using Ansible to automate infrastructure.

## Understand Ansible playbook.yml file

So, what is Ansible playbook.yml? Ansible playbook.yml is the infrastructure as code using YAML configuration language. This file describes all the infrastructure that will be created using the pipeline. The main idea here is that the continuous deployment pipeline needs the Ansible playbook so it can create the infrastructure needed to deploy the application and then pick up the package to deploy that package to the created infrastructure.

## Run and execute Continuous Deployment (CD) pipeline

Then, I will run the continuous deployment pipeline. The main idea here is that the pipeline will pick up the Ansible playbook which is the YAML file and then start running that remotely on the remote Ansible virtual machine. This execution will start creating the infrastructure described in the YAML playbook which will first create an Azure service plan, then MySQL database and then configure a firewall rule to allow the Azure web app to access the MySQL database. Once the infrastructure is created and ready, the pipeline will start picking up the Java package and then deploy that package to the web app which is a WAR file. Then it will extract all the Java files into the web app, so the web app now has all application files deployed.

## Open and browse the application

After that, I can open the web application from the browser and navigate to the hotel sample application and even log in to that and see all the data that loaded from the application and the database.

**Commands**  

```
Install Ansible commands  
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

\## Update and upgrade the packages  
sudo apt update && sudo apt dist-upgrade -y  
\## Install pre-requisite packages  
sudo apt install -y libssl-dev libffi-dev python-dev python-pip  
\## Install Ansible and Azure SDK via pip  
sudo pip install ansible\[azure\]  

Service principle and subscription IDs  
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

az ad sp create-for-rbac \--name ServicePrincipalRadwan  
az account show  

Authentication Remote Ansible machine to Azure  
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

mkdir \~/.azure  
nano \~/.azure/credentials  

Authenticate values  
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

\[default\]  
subscription_id=xxxx-xxxx-xxxx-xxxxx-xxxxxx-xx  
client_id=9093da51-a344-41b5-90f0-b13e255f3579  
secret=63ca3eef-11fd-41ef-a86a-717d65773d53  
tenant=xxxx-xxxx-xxxx-xxxxx-xxxxxx-xx  

Generate RSA key  
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

ssh-keygen -t rsa  
chmod 755 \~/.ssh  
touch \~/.ssh/authorized_keys  
chmod 644 \~/.ssh/authorized_keys  
ssh-copy-id mradwan@127.0.0.1  
cat \~/.ssh/id_rsa  

User name and password to log in to the hotel web app  
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--

Username: me@smarthotel360.com  
Password: 1234
```
