---
layout: post
title: "What's New in Visual Studio IntelliCode"
date:   2019-01-13 00:52:50 +0100
---

## Introduction

Visual Studio IntelliCode is a set of AI-assisted capabilities for Visual Studio to help make developers more productive. In this post, I am going to show the latest and greatest in [Visual Studio](https://visualstudio.microsoft.com/)[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/), which includes custom models and additional language support.

## Custom Models

Custom models will provide suggestions based on your code. The current model only provides suggestions for common types like strings or date/time things that are commonly found in the open source community. But now the classes that you use in your private code repositories will have AI-assisted intelligence suggestions. What is even better, is that once you train a custom model, you can go ahead and share that model with your teammates. They don't need to go through the same training process that you have already done.

How to get these custom models? In order to open the IntelliCode window, click on the View menu, then choose Other Windows, and click on IntelliCode. At the IntelliCode page, you will see the solution name and status of your model. To start the process, click on the "Train on my code" button, displayed in Image 1.

![Image 1 - Train on my code](/assets/images/2019/01/Image-1-Train-on-my-code-1024x578.png)
_Image 1 - Train on my code_

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan-devops.github.io/posts/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of the [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing "the big picture," while still maintaining a high level of detail.

### You will see the status page, with three possible statuses:

- Analyzing your code - happens all client-side, extracting all important information about your source code in order to feed it into our model service.
- Uploading your data - uploads all information to the service in the cloud.
- Learning your code's pattern (which is where the model is actually created) - after the model is generated, it is sent back down to Visual Studio to give you those starred recommendations of your custom types and classes.

After the model is quickly trained, you will see a new page all about your active trained model, displayed in Image 2.

![Image 2 - Active model](/assets/images/2019/01/Image-2-Active-model-1024x578.png)
_Image 2 - Active model_

On this page, the time and date it was trained are displayed, as well as its status, which shows that it is ready to be used. In addition, you have the ability to share it, as well as delete it if you do not want to use it anymore. If your code changes drastically from when you first created the model, you can retrain it. Also, the model details are displayed, with details about how many classes the model covers, and also recommendations.

> [More Info]{.ion-info} If you would like to learn more about the story behind containers and what drives the need for them, we will know why companies moved from traditional solution architecture to **Microservices** and how this makes containers the perfect solution for running them. We will get a quick intro to clarify some definitions, tools, and keywords related to this ecosystem, for example, we will understand the difference between VM, Container, and Hyper-V Container. Why we would prefer containers over VM and when the VM is better. We will understand the difference between container and image and know the lifecycle of creating a new image and why I do that, like adding more layers to the base image, pushing that to container images registry on the cloud, then pulling that from the registry to anywhere to have a new container. We will also understand different technologies and services around containers, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), Azure Container Registry, etc. - have a look at the [**this post**](https://mohamedradwan-devops.github.io/posts/containers-the-perfect-solution-for-running-microservices/).

## Additional Language Support

- Visual Studio
  - XAML
  - C++
- Visual Studio Code
  - JavaScript/TypeScript
  - Java

## Demo in Visual Studio Code

In [Visual Studio Code](https://code.visualstudio.com/) we can see there are two files opened, a Java file (Image 3) and a Python file (Image 4), which only has a message in it to start.

![Image 3 - Java file](/assets/images/2019/01/Image-3-Java-file-1024x578.png)
_Image 3 - Java file_

![Image 4 - Python file](/assets/images/2019/01/Image-4-Python-file-1024x578.png)
_Image 4 - Python file_

We are going to see that the AI-assisted [IntelliSense](https://docs.microsoft.com/en-us/visualstudio/ide/using-intellisense?view=vs-2017) is going to work seamlessly as I move between the Java file and the Python file. In the Java file, we have a simple message string. If you type "msg.", you will get AI-assisted IntelliSense suggestions (Image 5).

![Image 5 - AI-assisted suggestions - Java](/assets/images/2019/01/Image-5-AI-assisted-suggestions-java-1024x578.png)
_Image 5 - AI-assisted suggestions - Java_

If you move over to the Python file, just by clicking on the file (no extra setup), and activate AI-assisted IntelliSense. You will notice that Python IntelliSense works seamlessly without messing with the language server (Image 6).

![Image 6 - AI-assisted suggestions - Python](/assets/images/2019/01/Image-6-AI-assisted-suggestions-python-1024x578.png)
_Image 6 - AI-assisted suggestions - Python_

## Conclusion

IntelliCode saves you time by putting what you're most likely to use at the top of your completion list. IntelliCode recommendations are based on thousands of open source projects on [GitHub](https://github.com/) each with over 100 stars. When combined with the context of your code, the completion list is tailored to promote common practices.
