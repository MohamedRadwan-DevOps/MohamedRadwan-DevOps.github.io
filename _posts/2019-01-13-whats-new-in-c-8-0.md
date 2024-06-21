---
layout: post
title: "What's New in C# 8.0"
date:   2019-01-13 23:35:42 +0100
---

## Introduction

In this post, I am going to share some of the major features coming in [C# 8](https://blogs.msdn.microsoft.com/dotnet/2018/12/05/take-c-8-0-for-a-spin/). So far, all the new language features introduced in minor language versions of C# were designed not to have a large impact on the language. These features are mostly syntactic improvements and small additions to the new features introduced in C# 7.0.

## Null Reference Types

It would be nice to know ahead of time about a null reference exception, not when your customer sends the exception in a bug report. That is what null reference types are about as a feature. Essentially, null reference types are about solving the problem of finding out where null should be, where they should not be, and tracking where they will be or will not be. I am going to show you how to enable null reference types feature for the whole project in the source code. After enabling, it will give new warnings in existing code. Activate it by typing `#nullable enable` (Image 1).

![Image 1 - Nullable enable](/assets/img/2019/01/Image-1-Nullable-enable-1024x578.png)
_Image 1 - Nullable enable_

> You can see **[this video](https://www.youtube.com/watch?v=vev3Czaa1pA)** for more information about a walkthrough introducing the Release Management and Build Automation using TFS 2017/2015. Step by step, it covers the entire process, starting from creating the project, checking in the code into source control, creating a build definition, triggering the build, and creating a release pipeline. Learn how to configure the build steps properly, including Copy Files and Publish Build Artifacts. See how to create a new release definition, add environments, link to the build definition, and add tasks to the release definition, like Windows Machine File Copy, and configure them properly.

When you turn this feature on, all your reference types will be considered non-nullable.

## Async Streams

Async streams are the ability to have enumerators that support async operations, including new [IAsyncEnumerable](https://docs.microsoft.com/en-us/dotnet/api/microsoft.servicefabric.data.iasyncenumerable-1?view=azure-dotnet) and [IAsyncEnumerator](https://docs.microsoft.com/en-us/dotnet/api/microsoft.servicefabric.data.iasyncenumerator-1?view=azure-dotnet) interfaces. The language lets you await foreach over these to consume their elements and yield return to them to produce elements. It allows an async method to return multiple values, broadening its usability. The new proposed feature Async Streams in C# 8 removes the scalar result limitation and allows the async method to return multiple results. This change will make the async pattern more flexible so that you can retrieve data in a lazy asynchronous sequence from the database or download data in chunks when they become available.

## Range Syntax

It would be nice if we could specify a subrange or slice of an array with range syntax. For example, if we want to get from one to three from one array. It introduces a type Index, which can be used for indexing. You can create one from an int that counts from the beginning, or with a prefix `^` operator that counts from the end (Image 2).

![Image 2 - Range syntax](/assets/img/2019/01/Image-2-Range-syntax-1024x578.png)
_Image 2 - Range syntax_

It also introduces a Range type, which consists of two Indexes, one for the start and one for the end, and can be written with a `x..y` range expression. You can then index with a Range to produce a slice.

>If you would like to learn more about the story behind containers and what drives the need for them, we will know why companies moved from traditional solution architecture to Microservices and how this makes containers the perfect solution for running them. We will get a quick intro to clarify some definitions, tools, and keywords related to this ecosystem, such as the difference between VM, Container, and Hyper-V Container. Why we would prefer containers over VM and when the VM is better. We will understand the difference between container and image and know the lifecycle of creating a new image and why I do that, like adding more layers to the base image, pushing that to container images registry on the cloud, then pulling that from the registry to anywhere to have a new container. We will understand different technologies and services around containers, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), Azure Container Registry, etc. - have a look at this post - have a look at the [**this post**](https://mohamedradwan-devops.github.io/posts/containers-the-perfect-solution-for-running-microservices/).

## Recursive Patterns

An awesome feature, giving you the flexibility to test data against a sequence of conditions and perform further computations based on the conditions met (Image 3).

![Image 3 - Recursive patterns](/assets/img/2019/01/Image-3-Recursive-patterns-1024x578.png)
_Image 3 - Recursive patterns_

Switch expressions are added, which are a spiffed-up version of switches that are an expression form. An example of the same code from Image 3 but written with switch expressions is displayed in Image 4.

![Image 4 - Switch expressions](/assets/img/2019/01/Image-4-Switch-expressions-1024x578.png)
_Image 4 - Switch expressions_

## Implicitly Typed New Expressions

Implicitly typed new expressions enable the developer to omit the class name in a constructor when it can be safely inferred. In our example, we have several arrays of persons, and the type is repeated each time, although I am in a context where the type is clear (Image 5).

![Image 5 - Implicitly typed new expressions before](/assets/img/2019/01/Image-5-Implicitly-typed-new-expressions-before-1024x578.png)
_Image 5 - Implicitly typed new expressions before_

With this new feature, we can avoid this repetition, as shown in Image 6.

![Image 6 - Implicitly typed new expressions after](/assets/img/2019/01/Image-6-Implicitly-typed-new-expressions-after-1024x578.png)
_Image 6 - Implicitly typed new expressions after_

## Default Interface Members

This feature makes it easier to evolve interfaces. Once you publish an interface, you are already locked in because if you add another member to it, your implementations will break. We are now adding the ability to add members with a method body, which is unusual for interfaces, but it is going to be really useful. Because existing implementers like console.log can get the default implementation without having to change (Image 7).

![Image 7 - Default Interface Members](/assets/img/2019/01/Image-7-Default-Interface-Members-1024x578.png)
_Image 7 - Default Interface Members_

## Conclusion

There are many new features already in the works for C# 8. This post does not list all of them. Of course, other new features not mentioned in the post might be added to the language as well. With all that in mind, you should regard the information in this article only as an interesting glimpse into the potential future of the language.
