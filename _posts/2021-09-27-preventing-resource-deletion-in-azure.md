---
layout: post
title: "Preventing Resource Deletion in Azure"
date:   2021-09-27 23:46:13 +0100
---

When we build Azure resources, it doesn't mean that someone is not going to go in and delete it for us, or we also might accidentally delete something important just because we forgot that we weren't supposed to. Even if we are a [DevOps](https://mohamedradwan.com/posts/devops-tutorial-for-beginners-developing-ci-cd-pipelines-continuous-integration-and-deployment/) person or an Ops person, we may have sometimes the right to do it because sometimes we need to delete production resources, but we just want to prevent it to do by accident. 

For cases like this, there is a great tool within Azure which is called Locks, which locks some resources in order to prevent any modification or deletion. This post explains this new feature, preventing deleting production resources by accident. If we are deploying in a production environment, we may probably want to have some locks. Usually, we should generate some locks on every resource deployed in the production environment. It's up to us to take our templates or generate the templates and adapt them to our use case and constraint, but in both cases, the logs are automatically generated in a production environment. 

In order to check our locks (if there are any), we should go in our Azure Portal, open our Resource group, and navigate to the locks.

![Image 1 - Example Lock on resource](/assets/images/2021/09/Image-1-Example-Lock-on-resource.png)

Here we can see all existing locks for the current resource group. Also, here we can delete or edit the locks. 

The new thing in [NubesGen](https://www.nubesgen.com/) is adding support for the Bicep tool. With this, a lock module is generated for any resource group, creating a resource which is a lock to which we assign people to have the right to remove the lock itself.

![Image 2 - doNotDelete lock and roleAssignment](/assets/images/2021/09/Image-2-doNotDelete-lock-and-roleAssignment.png)

So we are doing two things here automatically. We are creating this "do not delete" lock, and we are assigning a role to some principle ID. So basically, to some user or to some service principle, we pass some parameters to do this. And we already leveraging here a cool feature of Bicep, which is conditions, which means that with spacing IF, meaning if this condition is met, then Bicep will actually deploy this lock. But if not, this code will not get deployed by Bicep or by Azure CLI.

![Image 3 - Condition for deploying the lock](/assets/images/2021/09/Image-3-Condition-for-deploying-the-lock.png)

So here is a cool thing to actually deploy locks only on the production environment. But obviously, we can reuse the feature to do a lot of different conditions in our infrastructure code. This gives us a lot of flexibility to say yes, we can lock down production. Maybe there are resource groups or other things that are very particular that we can't delete. And we all have worked on customer projects where we have almost a hub or an area that cannot be deleted because we can't repeat that code. 

Another cool feature is Soft Delete, which can be found in Data protection. There we can enable Soft delete for blobs. This feature enables us to recover blobs that were previously marked for deletion, including blobs that were overwritten. We can enable it for a specific time (in days), and some administrators can go back and restore the deleted blobs. This feature we enable if we really want to protect our data from accidental deletion at resource level or accidental deletion on API level.

Also, there are some limitations, or things that we should consider before applying locks. For example, a cannot-delete lock on a storage account doesn't prevent data within that account from being deleted or modified. This type of lock only protects the storage account itself from being deleted. If a request uses data plane operations, the lock on the storage account doesn't protect the queue, table, or file data within that storage account. However, if the request uses control plane operations, the lock protects those resources. A read-only lock on a storage account doesn't prevent data within that account from being deleted or modified. This type of lock only protects the storage account itself from being deleted or modified and doesn't protect blob, queue, table, or file data within that storage account.

It's important to understand that locks don't apply to all types of operations. Azure operations can be divided into two categories - control plane and data plane. Locks only apply to control plane operations. If you want to understand the resource locking in Azure Blueprints read this [article.](https://docs.microsoft.com/en-us/azure/governance/blueprints/concepts/resource-locking)

As an administrator, you can lock a subscription, resource group, or resource to prevent other users in your organization from accidentally deleting or modifying critical resources. The lock overrides any permissions the user might have.

In this post, you can find also an [Overview of some Azure Services (Part 1)](https://mohamedradwan.com/posts/overview-for-some-azure-services-part-1/)

Read more for Lock resources [here.](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json&wt.mc_id=devops-42208-cxa)
