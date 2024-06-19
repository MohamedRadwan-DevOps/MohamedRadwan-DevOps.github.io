---
layout: post
title: "Auto Scaling with Virtual Node and Azure Kubernetes Service"
date: 2019-01-18 01:56:15 +0100
---

## Introduction

In this post, we are going to talk about how to auto scale with AKS and a new public preview feature called Virtual Node. Virtual Node is now a public preview feature with [Azure Kubernetes Service](https://azure.microsoft.com/en-gb/services/kubernetes-service/). With Virtual Node, you can burst into Azure Container Instances (ACI) where you have no VM management. This enables you to scale your [Kubernetes](https://kubernetes.io/) clusters even faster when you combine concepts like the horizontal pod autoscaler. The technology behind this is Virtual Kubelet, which is an open-source project supported by multiple cloud providers.

## Background of Azure Container Instances

Sometimes, all you need to do is just run a container. VMs take up too much management for just trying to run a single workload, and that is why we need Azure Container Instances. They take away VM management, start in seconds, and support both Windows and Linux. They are also Hyper-V isolated, which means that you have the same level of isolation that you get in VMs today, just at the container level. You can also configure the amount of memory and CPU that you want.

## Going Through an Open Source Project - Virtual Kubelet

Virtual Kubelet is able to connect the Kubernetes APIs to any other kind of service. For Azure, it connects with Azure Container Instances, but there are also providers for IoT Edge and other services from Amazon, Hyper SH, and VMware. With ACI and Virtual Kubelet, AKS has built a preview called Virtual Node. In Image 1, the architecture of Virtual Node in AKS is shown.

![Image 1 - Virtual node architecture in AKS](/assets/images/2019/01/Image-1-Virtual-node-architecture-in-AKS.png)
_Image 1 - Virtual node architecture in AKS_

You get the management of a Kubernetes cluster, and the masters are already controlled for you because it is a managed control plane. You also get extra burst capacity through ACI and Virtual Node. Now you can have one to X amount of VMs in your cluster and then install Virtual Node in order to scale out (basically infinitely) into ACI. There are no VMs to think about. When you are scaling, you don’t have to scale VMs and then think about the workloads that go on top of them. All you do is scale out Azure Container Instances, and you don’t realize it because the management plane is still Kubernetes.

>If you would like to learn more about what is the story behind containers and what drives the need for them, we will know why companies moved from traditional solution architecture to Microservices and how this put containers as the perfect solution for running them. We will get a quick intro to clear some definitions, tools, and keywords related to this ecosystem. For example, we will understand the difference between VM, Container, and Hyper-V Container, why we would prefer container over VM and when the VM is better. We will understand the difference between container and image and know the lifecycle of creating a new image and why I do that. Like adding more layers to the base image, push that to container images registry on the cloud, then pull that from the registry to anywhere to have a new container. We will understand also different technologies and services around containers, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), Azure Container Registry, etc. - have a look at [this post](https://mohamedradwan-devops.github.io/posts/containers-the-perfect-solution-for-running-microservices/).
{: .prompt-info }

## Virtual Node in Public Preview

Let us see it in practice. I have already installed a Virtual Node in my cluster and installed an entire application. This application is a simple front-end that simulates a Black Friday event (selling service books, Xboxes). In other words, it is just a simple website. I started a big amount of load with a load tester, which is hitting the front-end a lot to see how our cluster scales with the demand of customer traffic. Now we are going to head over to Application Insights, which has a live metrics stream. Here, we can see the amount of incoming requests, how long the requests are actually taking, and the amount of servers that are coming up to handle the load (Image 2).

![Image 2 - Live metrics stream](/assets/images/2019/01/Image-2-Live-metrics-stream.png)
_Image 2 - Live metrics stream_

In addition, we are going to use another dashboard, Grafana, which is an open-source dashboarding tool. We can see that the RPS (requests per second) and RPS per pod are going exponentially up. On the other hand, the response time is actually going down because we are getting a bunch of more infrastructure starting up (Image 3).

![Image 3 - Grafana](/assets/images/2019/01/Image-3-Grafana.png)
_Image 3 - Grafana_

If we open the Azure Cloud Shell (Image 4), we can see the number of containers that are pending. This is where Kubernetes is stepping in and helping to auto scale out. We are using the horizontal pod autoscaler, which is a well-known feature in Kubernetes that allows you to horizontally scale out your pods.

![Image 4 - Azure Cloud Shell - pending containers](/assets/images/2019/01/Image-4-Azure-Cloud-Shell-pending-containers.png)
_Image 4 - Azure Cloud Shell - pending containers_

If we go back to the Live Metrics stream and refresh the page, we can see all of the container instances that are actually spinning up in the same resource group. We can note that many of them started up within a couple of seconds (Image 5).

![Image 5 - Container instances spinning up in the same resource group](/assets/images/2019/01/Image-5-Container-instances-spinning-up-in-the-same-resource-group.png)
_Image 5 - Container instances spinning up in the same resource group_

For this number of containers, you would probably need 5 to 10 VMs, all starting up one after another. But in our case, we just have 20 or 30 pods started up in tandem.

## Conclusion

You can use Virtual Nodes to auto scale out from your cluster into ACI, giving you an easy solution for scaling in Kubernetes. Virtual Nodes allow AKS users to make use of the compute capacity of Azure Container Instances (ACI) to fire up additional containers rather than having to bring up Virtual Machine (VM)-based nodes. It is, as Microsoft said, a simple act of flipping a switch to get access to all that resource.

>You can see this video, if you would like to find more information about how to get started with Release Management and its advantages. See how to create a build definition using CI/CD Tools for VSTS Extensions (I will be using Package Extension and Publish Artifact tasks). And also using DevOps-VSTS-POC trigger in order to enable CI. All of that to be able to publish, share, install, and query versions. You will see how to create a release definition, choose an artifact, and configure the source for the artifact and default version. See how to create different environments or clone the existing one, in my case, I am going to create QA, Preproduction, and Production environments, each with one phase and one task. See also how to configure the Publish Extension task for each environment. See an end-to-end continuous delivery pipeline using VSTS extension with Build and Release Management.
{: .prompt-tip }
{% include embed/youtube.html id='uGAcWLnSU0A' %}
