---
layout: post
title: "The next generation of Hockey App: Visual Studio Mobile Center (now Visual Studio App Center)"
date: 2018-04-22 22:31:21 +0100
---

## Introduction

[**Hockey App**](https://hockeyapp.net/) is part of **Microsoft**'s [**Mobile DevOps**](https://www.hockeyapp.net/best-practices/mobile-devops-devops-whats-the-difference.html) stack helping developers manage the app lifecycle and automate integration, testing, delivery, and monitoring. [**Mobile Center**](https://www.visualstudio.com/app-center/) is a new base for all of your mobile application needs. It is a set of [**DevOps**](https://mohamedradwan.com/posts/what-is-devops/) tools including continuous integration, automated UI testing, distribution, crashes, and analytics. You can use any number of these features independently, but the more you combine, the more powerful **Mobile Center** becomes.

## Mobile Center interface and services

>If you would like to learn more about enhancing frontend development code quality, it includes understanding different types of JavaScript unit testing frameworks like Jasmine, Mocha, Jest, different types of task runners like Grunt and Gulp, different types of linting tools like JSHint, ESLint, JSLint, CSSLint, different types of code formatters like Prettier and Tidy, how to write your first JavaScript using test with Jasmine standalone version, how to run JavaScript unit tests using Grunt, Command Line and PhantomJS.
How to calculate code coverage for JavaScript unit tests using Istanbul, how to run JavaScript unit tests using Visual Studio Test Explorer using chutzpah extension, how to lint JavaScript code using JSHint and how to run that from Command Line using Grunt, finally it shows how to integrate all the quality practices with Visual Studio Team Service Build automation so it can be part of CI/CD or Continuous Integration and Continuous Delivery - have a look at the [this post](https://mohamedradwan.com/posts/front-end-code-quality-javascript-unit-test-and-linting-automation-with-vsts-build/)
{: .prompt-tip }

**Mobile Center** provides you with an automated continuous integration process. The most important **Mobile Center** services are listed below:

1. **Getting Started** - contains some instructions about how to get started with the **SDK**.
2. **Build** - continuous integration service. Provides information about all the completed **Build**s and allows you to directly distribute **Build**s to a beta distribution group, and to download the different symbols and different logs.
3. **Test** - **UI** supports testing your devices on the cloud - i.e. testing common user scenarios on real devices.
4. **Distribution**
5. **Crashes**
6. **Analytics**

![1 - Mobile Center Interface and services](/assets/images/2017/12/1-Mobile-Center-Interface-and-services-1024x565.jpg)

## Transition from Hockey App to Mobile Center

To ensure a smooth transition from **Hockey App** to **Mobile Center**, **Microsoft** is providing a side-by-side viewing - when all your apps, organizations, collaborators, and testers coexist on both of these platforms. Your data will be synced back and forth, and any changes you make to **Hockey App** will automatically be delivered to **Mobile Center** and vice versa, ensuring consistency between the two services.

![2 - Side-by-side viewing with Hockey App and Mobile Center](/assets/images/2017/12/2-Side-by-side-viewing-with-Hockey-App-and-Mobile-Center.jpg)

>f you would like to learn more about what is the story behind containers and what drives or the needs for it, we will know why companies moved from traditional solution architecture to Microservices and how this put containers as the perfect solution for running them, we will get quick intro to clear some definitions, tools, and keywords related to this ecosystem. For example, we will understand what is the difference between VM, Container and Hyper-V Container, why we would prefer container over VM and when the VM is better, we will understand the difference between container and image and know the life cycle of creating a new image and why I do that, like adding more layers to the base image, push that to container images registry on the cloud, then pull that from the registry to anywhere to have a new container. We will understand different technologies and services around the container, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), Azure Container Registry, etc. - have a look at the [this post](https://mohamedradwan.com/posts/containers-the-perfect-solution-for-running-microservices/)
{: .prompt-info}

## Side-by-side collaboration tool

The side-by-side collaboration tool allows you to continue to use **Hockey App** but at the same time to start using **Mobile Center** and all the tools and improvements on existing services inside it. The tool is now available for **Hockey App** pre-season customers. To obtain access you have to perform the following steps:

![3 - Side-by-side collaboration tool installation](/assets/images/2017/12/3-Side-by-side-collaboration-tool-installation-1024x511.jpg)

## Conclusion

**Mobile Center** combines the lifecycle, monitoring, and backend features of **Microsoft**'s existing stack into a single platform. Nowadays, when quality is more important than ever, **Mobile Center** provides a robust crash-reporting solution analytics platform, enabling you to monitor the behavior and happiness of the customers. Moreover, **Mobile Center** is modular, which gives you the flexibility to use only the tools you need and nothing more.

>In order to ensure [**Continuous Integration**](https://www.visualstudio.com/team-services/continuous-integration/), we need to use proper **deploying strategy**. Read more about deploying with Feature Branches and Feature Toggle in the following post; [Deploy from Branches with and without Feature Toggle](https://mohamedradwan.com/posts/promoting-your-application-deployment-to-different-environments-from-branches-with-and-without-feature-toggle/).
{: .prompt-tip }
