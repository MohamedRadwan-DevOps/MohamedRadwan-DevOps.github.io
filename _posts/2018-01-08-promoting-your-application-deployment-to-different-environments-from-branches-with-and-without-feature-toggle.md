---
layout: post
title: "Deploy your Application to Different Environments from Branches with and without Feature Toggle"
date: 2018-01-08 00:42:25 +0100
---

[Introduction](#introduction) 
[Deploying Strategy with Feature Branches](#deploying-strategy-with-feature-branches) 
[Deploying Strategy with Feature Toggle](#deploying-strategy-with-feature-toggle) 
[Conclusion](#conclusion)

## Introduction {#introduction}

- Software development process required different environments for
  different purposes as we will see. Each environment should be isolated
  for different team roles to do their job and not accessed by other teams.
  But should still be similar in using the deployment workflow. Having a solid
  and well-defined deployment workflow is tremendously important if you
  want to have a smooth and solid deployment pipeline to production and
  follow the best practices for DevOps.


>For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginners](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**
{: .prompt-tip }
{% include embed/youtube.html id='4DUhc0MjdUc' %}

Lately, I've been hearing a lot about pros and cons about deploying with **Feature
Branches** in comparison to deploying with **Feature Toggle**. The
difference between two strategies is quite huge from many perspectives!
And still, both strategies are part of **Continuous Integration and Continuous Delivery Chain**.
Key importance to remember is that deployment should be considered as a part of the development process and not as an alternative or afterthought.
If you would like to know more about CI/CD you can look at my post:

[**Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)**](https://mohamedradwan-devops.github.io/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/)

If you want more focus on VSTS Release Management, you can see my video: [**Release Management and Build Automation with TFS/VSTS**](https://www.youtube.com/watch?v=vev3Czaa1pA&t=841s)

In this post, I will try to address key differences between both deployment
strategies, as well as the benefits and drawbacks of each. For the purpose of
having a good understanding of this post, we'll be using in both scenarios
the same environments: **Development**, **QA**, and **Production**. Let's
see first the differences between each environment:

![Dev_Environments](/assets/images/2017/12/Dev_Enviroments-1.png)

**Development environment** is where we'll be actually using the
whole set of processes and tools in order to create a product.
Developers can use their machines for the development environment or the
team can set the remote development environment, which allows
better flexibility and accessibility.

**QA** is often referred to as **Staging environment** and
it's the place where testers come into play and start verifying that the **Feature** works as intended.

**Production environment** is the last step in this chain and it
represents the environment where the **Feature** will be deployed
after testing. Usually, after **Feature** deployment from QA to
Production, its **Feature Branch** should be deleted.

## Deploying Strategy with Feature Branches {#deploying-strategy-with-feature-branches}

Deploying strategy with **Feature Branches** is an old but
still widely used deployment approach in software development. It's
known to be a pretty simple approach where you have the ability to
organize coding in a way to have simple tracking of work in progress
with already completed code that has been completed and tested.

If we consider the environments as presented above, the workflow of
deployment with **Feature Branches** would look like this:

![Feature_Branches](/assets/images/2017/12/Feature_Branches-2.png)

To understand this workflow diagram, I will explain each step:

1. Developer or group of developers will be working on **Features** (it
   could also be on bugs) in separate **Feature Branch**. Let's
   say that one developer is working on a **Feature** called "Display
   navigation bars in Admin area". The second developer is working on
   a **Feature** called "Display product list" and the third developer
   is working on a **Feature** called "Display grid view for lists".

2. When the **Features** are implemented they will be deployed into
   the **QA** or **Staging environment** for quality assurance.

3. After successful completion of testing, the **Feature Branch**
   will be merged into the **Development Branch**.

4. When the release is ready, the development **Branch** will be
   merged into the **Master Branch** and then deployed into the
   **Production environment**.

This practice is commonly used as it gives the team the flexibility
to deploy to the production only **Features** that are fully developed
and tested. If the team has only 1 **Feature Branch**, which is
ready for release, they will only merge this 1 **Feature Branch** to
the **Master Branch** and then deploy it to production. In this case,
the team will be continuing the development work on other 2 **Branches**
and they will merge them with **Master** and include in future releases.
As you can probably understand by now the philosophy behind
**Feature Branches**, the purpose is to isolate the code for each
**Feature** until the code is fully developed and ready for release.

>For more information about how to work with **Docker** like pulling docker
images, running docker images, and working with containers, see **[Docker for
beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)**
{: .prompt-tip }
{% include embed/youtube.html id='3RJv6yVfaRE' %}

### Like Windows Machine File Copy and configure it properly.

One of the major problems in development by **Feature Branches**
is that every time when a **Feature Branch** is ready for
release, it will be prior to release merged into the **Master Branch**.
This will cause a really big **Changeset** in the main **Branch**,
which means that all other **Feature Branches** will also need to merge
that huge **Changeset** back with their **Feature Branches**.
Developers working on their **Feature Branches** will feel the pain of merging their changes.
In many cases, the team refuses to merge their changes with the **Master Branch**.
Because this can cause them too much pain in merging what they have developed so far with the **Master**.
This resistance is opposed to CI as there is no frequent integration between the code,
which means a couple of steps back in development.

## Deploying Strategy with Feature Toggle (Feature Flag) {#deploying-strategy-with-feature-toggle}

**Feature Toggle**, which is often referred to as **Feature Flag**, is a really good alternative to development and deployment by
**Feature Branches**. **Feature Flag** will avoid some of the
drawbacks coming from **Feature Branches**.

What does it basically mean? Let's see the image below:

![Feature_Toggle](/assets/images/2017/12/Feature_Toggle-1.png)

As you can see, it means that we will do all the work in one single
**Branch**. Where we'll use mechanisms that will enable turning on or
off specific **Features**. This is usually done via a config file. The
workflow diagram in this case is completely different. All developers
will work on the same **Branch** and they will include and enable
**Feature Toggles** in their config files. Once the development
of the **Feature** is finished, they will simply remove all entries
for the **Feature Toggle** as their last step before merging to the
**Master Branch**.

### Build once and promote the same artifacts to different environments

For developers, this would mean that they would simply be building the
code just one time and they will not build the code for each environment
or branch. They will build the code just once, merge it to the master branch, and from there they will deploy the same code first to the Development environment, then to the QA environment, and finally to the Production environment.

**It should be like the following:** Develop → merge to master → build → upload to storage → deploy to Dev → test → approve → deploy to QA → test → approve → deploy to Pre-Prod → test → deploy to Prod

### Don't map branches to environments

Using a strategy with **Feature Toggles** means that branches are not
linked directly to environments. which was mentioned in the previous way of
deployment. When we use feature branches with a middle litigation branch
(dev branch), promoting or moving the code from one
environment to another will be implemented with deployment tools not
with different branches. In the previously explained strategy, for example, we
would be promoting code by branch merging. Using **Feature Toggles**
means that we are always promoting the same code (branch) through
different environments. The same code or the same artifacts go through
all staging environments. We deploy code to the environment, test it, and
deploy the same code to the next environment, where we again test the same
code and deploy it to the next environment.

### With Feature Toggle, it avoids merge conflicts with the master branch after test complete

Another important aspect to avoid getting later errors for what we
already tested is the recommendation to consider the QA stage for complete
product testing and not only individual features. Testing only
individual features in isolation will bring us to think that we have
good quality code while there are actually some merging or
integration errors existing that we didn't even know about.

### With Feature Toggle, you can disable the feature that you can't fix and don't delay the release

The main goal of the Feature Toggle is that since we are using the same
branch, and if we have some bugs related to a particular feature and we
don't have enough time for our release or cadence, we can switch it off
so we can release our cadence and not delay it.

## Using Feature Toggle after release

Another important point that I would like to mention here is the
rollback if something goes wrong after the release. Previously, I've
mentioned that developers can remove the **Feature Toggle** in their
config file prior to merging to the **Master Branch**. This doesn't
necessarily have to be the case, as they can leave **Feature Toggle**
mechanisms just the way they are in order to turn off the
**Feature** even after the release. This gives the team full
independency in fixing the **Feature** without impacting other
**Features**, without having to roll back the whole version.

![Feature_Toggle_on_off](/assets/images/2017/12/Feature_Toggle_on_off.png)

With **Feature Toggles**, we also have the possibility to target
just a specific group of people or specific areas. For example, we can
turn on or off the **Feature Toggle** for specific users of your
system, such as beta users or we can target just specific geographic
areas or countries.


>For more information about how to work with **Git** with animation. All commands will be represented in graphical animation, e.g., git branch, git merge, git rebase, git cherry-pick, and many others, see **[Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)**
{: .prompt-tip }
{% include embed/youtube.html id='ZgCCnv9LxzA' %}


## Conclusion {#conclusion}

Both strategies have their pros and cons. At the end, it depends also
on team preferences with which strategy they will feel more
comfortable to ensure Continuous Integration. As a part of being an MVP, I
know for a fact that Microsoft uses **Feature Toggles** broadly.
Many of Microsoft's new **Features** are turned on just for MVPs on the
Microsoft team to get quick feedback on the newly built
**Features**. This new direction has been present inside VSTS for some
time now and it gives both sides, users and developers, insights about
the development direction.
