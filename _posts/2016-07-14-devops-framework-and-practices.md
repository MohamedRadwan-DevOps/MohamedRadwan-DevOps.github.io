---
layout: post
title: "DevOps Framework and Practices"
date:   2016-07-14 13:42:49 +0100
---

### Introduction 

**DevOps** is a methodology that refers to anything that settles the
interaction between development and operations. Development needs as
much changes as possible to grow and to meet the needs of the changing
time while for Operations change is the enemy. Operations require
stability and strongly resist change that is a need for Development. 

>You can find more information about **DevOps** in the
following post: [DevOps: The Three Stage Conversation - People, Process,
Products](https://mohamedradwan-devops.github.io/posts/devops-the-three-stage-conversation-people-process-products/)
which describes the basic principles of **DevOps**. This post will be
especially helpful to those for whom DevOps is still a new concept. If
you prefer a deeper view on this topic, have a look at the following
guide: [quick guide about Basic Principles of
DevOps](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-basic-principles-of-devops/),
which presents an overview of
[DevOps](https://www.visualstudio.com/vs/devops/) process and practices,
describing \"the big picture\", while still maintaining the high level
of detail.
{: .prompt-tip}

>If you would like to know more about the best
practices for
[DevOps](https://www.visualstudio.com/team-services/devops/), Continuous
Integration and Continuous Delivery, you can have a look at the
following post: [Configure CI (Continuous Integration) and CD
(Continuous Delivery
Pipeline)](https://mohamedradwan-devops.github.io/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).
{: .prompt-info }

### Part 1: DevOps Frame 

**DevOps** is a strategy intended to bring perfection in software
delivery lifecycle by aligning development and Operations teams around
the business goals. As per Microsoft\'s standard level definitions
[DevOps Level 100](https://www.microsoft.com/en-us/download/details.aspx?id=50826) is introductory and overview material. It
covers topic concepts, functions, features, and benefits. **DevOps Level 200** is intermediate material. Assumes 100-level knowledge and provides
specific details about the topic. **DevOps Level 300** is advanced
material. Assumes 200-level knowledge, in-depth understanding of
features in a real-world environment, and strong coding skills. Providess
a detailed technical overview of a subset of product/technology
features, covering architecture, performance, migration, deployment, and
development. 

![1- DevOps Framework](/assets/img/2016/07/1-DevOps-Framework.jpg "1- DevOps Framework")

>In order to ensure [**Continuous Integration**](https://www.visualstudio.com/team-services/continuous-integration/) 
we need to use proper **deploying strategy**. Read more about deploying
with Feature Branches and Feature Toggle in the following post; [Deploy
from Branches with and without Feature
Toggle](https://mohamedradwan-devops.github.io/posts/promoting-your-application-deployment-to-different-environments-from-branches-with-and-without-feature-toggle/).
{: .prompt-tip}

You can see this video, if you would like
to find more information about what is the story behind containers and
what drives or the needs it, we will know why companies moved from
traditional solution architecture to Microservices and how this put
containers as the perfect solution for running them, we will get quick
intro to clear some definitions, tools and keywords related to this
ecosystem, for example, we will understand what is the different between
VM, Container and Hyper-V Container.
{: .prompt-tip}
{% include embed/youtube.html id='18i94MfJSAI' %}

why we would prefer container over VM and when the VM is better, we will
understand the different between container and image and know the life
cycle of creating a new image and why I do that, like adding more layers
to the base image, push that to container images registry on the cloud,
then pull that from the registry to anywhere to have a new container. We
will understand how the orchestration and clustering work for containers
by managing the underline nodes which host the containers. We will
understand also different technologies and services around container,
like Docker, Docker Hub, Docker Swarm, Kubernetes, Azure Container
Services (AKS), Azure Container Registry.

### Part 2: DevOps Practices 

There are many fundamental **DevOps practices**. Few of them are listed
below: **Infrastructure as Code (IaC)** is the practice in which the
techniques, processes, and tool sets used in software development are
leveraged to manage the deployment and configuration of systems,
applications, and middleware. Most of the testing and deployment defects
occur when developer\'s environments differ from testing and production
environments. Putting these environments under version control yields
immediate benefits in consistency, time savings, error rates, and
auditability. Under **Continuous Integration (CI)** practice, the
working copies of all the developers code are combined with a shared
mainline. **Automated Testing** - is the practice where various tests
such as load, functional, integration, and unit tests happen
automatically either after you check in code (i.e. attached to CI) or
some other means to fire off one or more tests automatically against a
specific build or app. **[Release management](https://mohamedradwan-devops.github.io/posts/release-management-overview-for-tfs-and-vsts/)** is a practice intended to oversee the
development, testing, deployment and support of software releases.
**Configuration Management** is the practice for establishing and
maintaining consistency of a product\'s performance with its
requirements, design and operational information throughout its life.

![2- DevOps Practices](/assets/img/2016/07/2-DevOps-Practices.jpg "2- DevOps Practices")

>You can see this video, if you would like to find more information about how to get started with
Release Management and its advantages. See how to create a build
definition using CI/CD Tools for VSTS Extensions. (I will be using
Package Extension and Publish Artifact tasks), and also using
DevOps-VSTS-POC trigger in order to enable CI. All of that in order to
be able to publish, share, install and query versions. You will see how
to create release definition. Choose an artifact and configure source
for the artifact and default version. See how to create different
environments or clone the existing one. In my case I am going to create
QA, Preproduction and Production environment. Each with one phrase and
one task. See also how to configure Publish Extension task for each
environment .See an end-to-end continuous delivery pipeline using VSTS
extension with Build and Release Management.
{: .prompt-tip}
{% include embed/youtube.html id='uGAcWLnSU0A' %}


>If you would like to know more about Azure deployments,
have a look at the post [How to deploy to Azure using Team Services
Release
Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/).
The post describes how Azure deployments are made easy by using Visual
Studio Team Services (VSTS) Release Management. You will see a
step-by-step tutorial on how to configure and deploy to Azure in Release
Management, and, moreover, how to configure an end-to-end pipeline for
deploying applications on Azure.
{: .prompt-tip}


### Conclusion

**DevOps** is all about better delivery practices, automation, removing
bottlenecks and is **Agile** at Organization level. **DevOps** is not a
tool. It cannot be built or achieved in a day or a month. It is a path -
a roadmap that needs to be followed. -�

>In one of the old posts [TFS 2015 Agile Project
Management](https://mohamedradwan-devops.github.io/posts/tfs-2015-agile-project-management/)
you can read more about new [**Agile Project
Management**](https://docs.microsoft.com/en-us/vsts/work/backlogs/overview)
features in **TFS 2015,** which provide better support for aligning
across teams, while giving autonomy to individual teams; you can use the
same structure with VSTS/TFS2018.
{: .prompt-tip}




You can see **[this video](https://www.youtube.com/watch?v=RjTMygBvWMM%20)**, if you would
like to find more information about some problems of Windows Azure
concerning the Credit Status in the case of high configuration hardware,
and possible solutions to these problems. Rather than reducing the
configuration of the machine. A method of closing the machine with the
aim of reducing computer hours while keeping the high configuration is
proposed.

The video demonstrates how to create an automation to close virtual
machines and reopen them at a required point in time. In particular the
following processes are explained: how to add a new Global Admin user in
the Default Active Directory. How to Create a new Automation and the
Assets for it.++ And How to create and run Runbooks,++ To create a
schedule and associate it with a runbook.++ How to set the Runbook script
to retrieve and execute the credentials and how to change the script to
keep a certain VM. (in this case the domain controller) running.
{: .prompt-tip}
{% include embed/youtube.html id='RjTMygBvWMM' %}


