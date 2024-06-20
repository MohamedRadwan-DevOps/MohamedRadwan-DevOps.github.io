---
layout: post
title: "Getting Started with Kubernetes Cluster | CI-CD for Azure Kubernetes Service"
date: 2019-06-08 09:37:29 +0100
---

Getting Started with Kubernetes Cluster with CI-CD for Azure Kubernetes Service. In this post, you will learn how to start with Kubernetes Cluster and how to build CI-CD for Azure Kubernetes Service (AKS). 

[Watch the video](https://www.youtube.com/watch?v=4DUhc0MjdUc)

Learn how to configure **CI/CD pipelines** to automatically push a docker image to a Kubernetes cluster abstracted by Azure Kubernetes Services (AKS). Learn how to pull a docker image from a public container registry, deploy your application to the docker image, then push the image to a private container registry to get ready to be picked up by the release pipeline.

Kubernetes cluster is considered to be a very important containerization orchestration system or platform in the industry now. Azure Kubernetes Services (AKS) is the fastest way to use Kubernetes on Azure to deploy a multi-container application. In this video, we will learn and understand all these topics and how they are connected.

Some points that will be covered in the video:
- A quick overview of Kubernetes cluster, what is a pod, what is a node, and how the **[Kubernetes](https://kubernetes.io/) cluster** structures pods and nodes.
- A full demo workflow in animation to understand the steps of the demo, followed by a walk-through of the end-to-end scenario.

>For more information about how to work with **Git** with animation. Each command will be represented in graphical animation. E.g. git branch, git merge, git rebase, git cherry-pick, and many others, see [Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/).
{: .prompt-info }

**So, what is Kubernetes?** Kubernetes is an open-source containerization orchestration system for automating deployment, scaling, and management of containerized applications.

### Key advantages of Kubernetes:

- Deploy your applications quickly and predictably
- Improves reliability
- Continuously monitors and manages your containers
- Scales your application to handle changes in load on the fly as needed
- Better use of infrastructure resources by limiting hardware usage to required resources only, which helps reduce infrastructure requirements by gracefully scaling up and down your entire platform
- Coordinates what containers run where and when across your system
- Easily coordinates deployments of your system

**All these advantages make Kubernetes:**

- **Portable** (Public, private, hybrid, multi-cloud)
- **Extensible** (Modular, pluggable, hookable, composable)
- **Self-healing** (Auto-placement, auto-restart, auto-replication, auto-scaling)

### So why use Azure Kubernetes Service?

Azure Kubernetes Service (AKS) is the quickest way to use Kubernetes on Azure. It manages your hosted Kubernetes environment, making it quick and easy to deploy and manage containerized applications without container orchestration expertise.

**Key advantages of Azure Kubernetes Services (AKS):**

- Hosts your Kubernetes environment
- Quick and easy to deploy
- Hosted control plane
- Manages containerized applications without container orchestration expertise
- Continuous build option that creates Docker images for faster deployments and reliability
- Create resources and infrastructure inside the Azure Kubernetes cluster through Deployments and Services manifest files

>For more information about how to work with **Docker** like pulling docker images, running docker images, and working with containers, see [Docker for beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/).
{: .prompt-info }

**Docker for beginners** 

It also eliminates the burden of ongoing operations and maintenance by provisioning, upgrading, and scaling resources on demand, without taking your applications offline. One of the biggest advantages of using AKS is that instead of creating resources in the cloud, you can create resources and infrastructure inside the Azure Kubernetes Cluster through Deployments and Services manifest files.

Azure Kubernetes Service is a fully managed Kubernetes orchestration service with auto patching, auto scaling, and auto updates. It uses the full Kubernetes ecosystem (100% upstream) and is deeply integrated with Azure Dev Tools and services. This video also covers how to grant access to Azure Kubernetes Service to communicate with Azure Container Registry. During the creation of the Azure Kubernetes Service, it will create a Service Principal which will be used to create a Role assignment using the Service Principal ID and Azure Container Registry ID. The main idea is to have authorization between Azure Kubernetes Service and Azure Container Registry. Azure Pipelines must also have authorization for both. Watch the video for more details.

### Commands used in the video:

```
version=$(az aks get-versions -l "West Europe" --query 'orchestrators[-1].orchestratorVersion' -o tsv)

az group create --name AKSRG --location "West Europe"

az aks create --resource-group AKSRG --name aksmohamedradwan --enable-addons monitoring --kubernetes-version $version --generate-ssh-keys --location "West Europe"

az acr create --resource-group AKSRG --name acrmohamedradwan --sku Standard --location "West Europe"

CLIENT_ID=$(az aks show --resource-group AKSRG --name aksmohamedradwan --query "servicePrincipalProfile.clientId" --output tsv)

ACR_ID=$(az acr show --name acrmohamedradwan --resource-group AKSRG --query "id" --output tsv)

az role assignment create --assignee $CLIENT_ID --role acrpull --scope $ACR_ID

az sql server create -l "West Europe" -g AKSRG -n sqlmohamedradwan -u sqladmin -p P2ssw0rd1234


az sql db create -g AKSRG -s sqlmohamedradwan -n mhcdb --service-objective S0


az aks get-credentials --resource-group AKSRG --name aksmohamedradwan

kubectl get pods

kubectl get service mhc-front --watch
 az aks install-cli

set PATH=%PATH%;C:\Users\mohamed.radwan\.azure-kubectl (for the current session) or copy it to Env vars

kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard

kubectl delete clusterrolebinding kubernetes-dashboard -n kube-system

az aks browse --resource-group AKSRG --name aksmohamedradwan


az aks scale --resource-group AKSRG --name aksmohamedradwan --node-count 3 

az aks upgrade --resource-group AKSRG --name aksmohamedradwan --kubernetes-version 1.14.0
```

