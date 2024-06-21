---
layout: post
title: "Requirements (Epic, Feature, User Story), Task Size and Estimation in Agile and Scrum"
date:   2017-12-05 11:00:27 +0100
---


## Introduction

Having the right size for the **Backlog items** and the tasks is crucial for smooth and successful sprint delivery. **Agile and Scrum** is a **User Story** or **Product Backlog Item (PBI)** driven approach, and this approach overcomes some of the major challenges in delivering the product that the customer seeks.

![Portfolio_Backlog](/assets/img/2017/11/itemContent.jpg)

Usually, there is a huge gap between customers and the people responsible for building the product. But still, in order to create a successful product, both sides should communicate with each other in the most efficient way. This implies that communication and understanding the requirements are crucial in delivering the product that the customer has envisioned.

This post will briefly describe some of the practices I have captured while visiting some of my customers and also some of the practices I recommend to consider when defining the requirements, within the usage of [**VSTS**](https://mohamedradwan-devops.github.io/posts/vsts-dashboards/).

## Product Planning

The first step you would want to do is to discuss the high-level plan with your customer, which will be your first input. Here is where you will need to understand the high-level plan and later, more detailed **requirements** in order to be able to dis-aggregate the plan into smaller items.

Remember, if you are building the product for a customer, this division is done based on the information you currently have at hand. Of course, if you are building the project for yourself, many of the requirements will be clear, or at least you will think they are clear in this phase.

However, [**VSTS**](https://docs.microsoft.com/en-us/vsts/work/work-items/guidance/cmmi/arrange-requirements-into-a-product-plan) allows users to plan and structure the project based on their needs. But there are still some key points you would want to consider while planning the delivery of the product. The user story should be Independent, **Estimable**, **Small**, and **Testable** (among other criteria). It should be considered an item that should be delivered in days. With this in mind, you can start building your product [**Backlog**](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/) around this idea.

### If the user story, which is in **VSTS** captured as [**PBI (Product Backlog Item).**](https://docs.microsoft.com/en-us/vsts/work/backlogs/create-your-backlog)

is delivered in days, then we should map the user story to a feature which will usually be delivered in weeks. A small remark: when I am referring to "being delivered", I am referring to delivering a fully working piece of product or service. This means that this item has been tested and it meets all the requirements for deployment to production. Furthermore, it means that there are no dependencies and that this item can be used as a completely independent piece of product with its full functionality.

Having this in mind, and if you have already faced the structure of the **VSTS Backlog**, you may already understand the following structure:

#### Epic -> Months
#### Feature -> Weeks
#### User Story/PBI -> Days

![Requirements size- Epic-Feature-PBI-User Story-Task](/assets/img/2017/11/Requirements-size-Epic-Feature-PBI-User-Story-Task-1.png)

What this means is that we usually use **Epics** as items that will be fully delivered in months, **Features** as items that can be delivered in weeks, and **User Stories** or **PBIs** as items that can be delivered in days.

![VSTS backlog-Epic-Feature-PBI-Bug](/assets/img/2017/11/VSTS-backlog-Epic-Feature-PBI-Bug-1.png)

>If you want to know more about maintaining the backlog properly, you can visit the following post: [Key Tips For Maintaining Good Product Backlog in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/). The post describes a way to efficiently organize the [backlog](https://docs.microsoft.com/en-us/vsts/work/backlogs/create-your-backlog) items, allowing you to understand the requirements better and providing you with a higher level of detail on what is actually expected from the work or delivery perspective.
{: .prompt-info}

Bear in mind that if your project goes further than presented above, you will be able to add additional levels to your product backlog. Please see the picture below for more insights about the levels and structure that can be adjusted in **VSTS** to achieve the desired product management. In total, you can have seven levels, starting from the very top and going to the task level.

![five-levels-portfolio-backlogs](/assets/img/2017/11/five-levels-portfolio-backlogs.png)

## Sprint planning

Once you reach the point where you start to work on the user story, you will want to consider cutting the user story into smaller tasks. There are many reasons why you would want to slice the user story or **PBI** into a **Task**. One reason is that this particular user story will not be developed just by one person or developer or even a pair of developers. In many cases, one **PBI** or **User Story** is developed by two or more developers or people who specialize in a certain part of the **User Story**. In this case, slicing the **User Story** into a **Task** will be the fastest and most efficient way to deliver it.

In **VSTS**, using the [**Agile**](https://mohamedradwan-devops.github.io/posts/quick-intro-to-agile/) approach, we usually use tasks as items that can be delivered within hours and are shared between different developers.

#### Task -> Hours

## Planning Poker

There are many estimation techniques that different teams use to estimate the effort to complete work items, and **Planning Poker** is one of the widely used ones. In the **Planning Poker session**, the team will usually have a short discussion about requirements to make sure everyone understands them very well. After that, each team member will estimate the effort that could be spent delivering that work item. A crucial point here is that the team needs to understand well all the work items to estimate them accurately. If the team doesn’t understand the requirements well, they cannot then make a good estimation. The team will not use time duration for this estimation, but they will use **story points**, which can use a scale like the [**Fibonacci sequence**](https://en.wikipedia.org/wiki/Planning_poker), t-shirt sizes as XS, S, M, L, XL, XXL, or even a custom-made scale.

![Planning poker with story points and t-shirt size](/assets/img/2017/11/Planning-poker-with-story-points-and-t-shirt-size.png)

The **Planning Poker** usually involves all the team or teams, as each team or member will see the estimation from their perspective. For teams using [**VSTS**](https://docs.microsoft.com/en-us/vsts/user-guide/what-is-vsts), there is also a [**Planning Poker extension**](https://marketplace.visualstudio.com/items?itemName=ms-devlabs.estimate), which will bring great benefits for the estimation part. As the extension is a part of **VSTS**, it will automatically transfer the agreed story points directly onto the work items.

## Backlog Estimation and Sizing Techniques

Recommended backlog estimation techniques are different for different levels of backlog. The picture below shows that it’s recommended to estimate items on a higher level, which have a bigger scope and belong to portfolio backlog items with t-shirt sizes, such as XL, L, M, etc. The items on the high level are many times associated, for example, with the cost range (e.g., a small project will cost between $10k and $25k). In this way, we can think about effort in a more abstract way. When we move to the next level on the product backlog, it’s more convenient to estimate items in story points, as they will be the best option for estimation when considering team members with different skills. For example, two programmers of differing productivity will be able to agree with story points estimation about the amount of work, the complexity, and the possible risks. If we go to the Sprint level, we need to consider the team’s capacity, which is measured in hours, and for this reason, it’s convenient to estimate tasks in hours.

![Recommended Estimation for Backlog Theme Epic Feature User Story and Tasks](/assets/img/2017/12/Recommended-Estimation-for-Backlog-Theme-Epic-Feature-User-Story-and-Tasks.png)

## Conclusion

Every project should, of course, have a tailored and well-customized **Backlog** that will fully capture all the requirements and be able to show the progress of the project. But as explained in this post, there are some basic guidelines that you might want to consider when building a product backlog within **VSTS**.
