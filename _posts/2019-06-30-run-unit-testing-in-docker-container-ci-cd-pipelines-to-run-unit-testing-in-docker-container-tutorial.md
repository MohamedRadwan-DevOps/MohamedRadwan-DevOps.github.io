---
layout: post
title: "Run Unit Testing in Docker Container | CI/CD Pipelines to Run Unit Testing in Docker Container Tutorial"
date: 2019-06-30 08:51:48 +0100
---

How to run Unit Test in Docker Container with and without CI/CD pipeline

## Intro

So, you will see and learn how to run unit testing manually in a [docker](https://www.docker.com/)container. Also, how to run them as a part of the CI/CD pipeline. All the content of this post with more details is explained in the following video:
{% include embed/youtube.html id='p-x_F6WMOgw' %}

## Run unit testing in 3 different ways

So, I will explain to you how to run unit testing in 3 different ways:

1. Run unit testing as everything manually
2. Run unit testing manually but with dockerfile
3. Run unit testing fully automated as part of the CI/CD pipeline.

## Run unit testing as everything is manually (Overview)

I will manually do step-by-step to copy and run everything. Starting by command line with an interactive mode within a container, then do all the steps manually to run the unit testing. We don't do that in real life, the main idea here or the main reason is to understand what is happening behind the scene.

## Run unit testing manually but using dockerfile (Overview)

As you now understand all the manual steps, we will put all those manual instructions into or inside a dockerfile, then build a container image based on that dockerfile. I will not even build all the instructions from one dockerfile in one time; instead, I will build the docker image based on the dockerfile incrementally, line by line. So, you can understand deeply and exactly how the dockerfile is structured, executed, and what the results of that execution are.


>For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**.
{: .prompt-tip }
{% include embed/youtube.html id='4DUhc0MjdUc' %}



## Run unit testing fully automated as part of the CI/CD pipeline (Overview)

As you now understand all the manual steps, including the [dockerfile](https://docs.docker.com/engine/reference/builder/)execution, let's run unit testing as part of the build automation pipeline. Let's see how to hook this up and automate all those steps into the CI/CD pipeline.

## Run unit testing as everything manually (Details)

I will start by creating a sample application with two unit tests, one passed and one failed. These are just very simple unit tests; they don't even include any code. This is why I will put in the second unit test throwing an exception to force this unit test to fail. Then, I will copy my application to a unit test remote host machine, which I created on the cloud. This machine will run the docker container. Then, I will run the container and copy my application from the remote local machine to the running container. As my application is inside the container, open the container in interactive mode. From the command line, start by typing the command to restore the third-party package or NuGet packages of my application. Then, from the command line, type the command to execute to build the application and execute the unit testing.


>For more information about how to work with **Git** with animation. All commands will be represented in graphical animation. E.g., git branch, git merge, git rebase, git cherry-pick, and many others, see **[Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)**.
{: .prompt-tip }
{% include embed/youtube.html id='ZgCCnv9LxzA' %}

## Run unit testing manually but using dockerfile in details (Details)

I will start this method by creating a dockerfile, which runs the unit tests inside the docker container, then builds the image from the dockerfile, then runs the container from the new image created. Now my image has the application, the unit tests, and the unit testing executed. Then, I will see the test results stored in that image.

## Run unit testing fully automated as part of the CI/CD pipeline in details (Details)

I will push the application to a remote repo on [Azure repo](https://azure.microsoft.com/en-gb/services/devops/repos/){target="_blank" rel="noopener noreferrer"}, then create a dockerfile in Azure Repos for the Azure pipeline. After that, I will configure the build definition to use that dockerfile to run the unit tests as a part of the build automation and see the test results as a part of the build or CI pipeline execution.


For more information about how to work with **Docker** like pulling docker images, running docker images, and working with containers, see **[Docker for beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)**.
{: .prompt-tip }
{% include embed/youtube.html id='3RJv6yVfaRE' %}

