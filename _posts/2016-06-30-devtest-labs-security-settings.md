---
layout: post
title: "DevTest Labs security settings"
date: 2016-06-30 15:03:42 +0100
---

### Introduction

I've described in general what **DevTest Labs policies** are in a previous blog post [Quick overview of Azure DevTest Labs](https://mohamedradwan-devops.github.io/2016/06/29/quick-overview-of-azure-devtest-labs/). Access for **DevTest Labs** is controlled by [Azure Role-Based Access Control (RBAC)](https://azure.microsoft.com/en-us/updates/general-availability-role-based-access-control/). If you are the owner of a specific Lab, you can apply security access settings using two lab roles: **Owner** and **User DevTest Lab Role**. The **Owner** role has full access including management and monitoring functions. It is very important to emphasize the distinction between these roles in the lab. If the owner is assigned the **User** lab role, this role doesn’t have the permissions to access resources in the subscription outside the lab scope. But in the opposite case, when the **User** is assigned the **Owner** role, they can automatically have the **Owner** rights to all created resources in that subscription. The **User** role is very limited. This role can only create **VMs**, delete only their **VMs**, and connect only to their created **VMs**. This post will describe a step-by-step tutorial for setting **DevTest Labs security settings** and provide a detailed description of role functionalities.

### Step 1: Add new User in DevTest Labs 

A user can be either an internal user with an **[Azure Active Directory subscription](https://azure.microsoft.com/en-us/pricing/details/active-directory/)** or external, who doesn’t have an **Azure Active Directory subscription**.
1. In your **Lab**, click on **Settings**.
2. From the list of users, choose **Users** to add a new user.
3. Click on the **Add** button.

![1-1 Add new User in DevTest Labs](/assets/images/2016/06/1-1-Add-new-User-in-DevTest-Labs.jpg "1-1 Add new User in DevTest Labs"){.alignnone .wp-image-6309 width="763" height="404"}

4. In the **Add Access** blade, click on **Select a role**.
5. In the **Select a role** blade, click on **DevTest Lab User**.
6. When a new blade appears, click on **Add Users**.
7. Type the **email address** of the **User**, which can also be an external user as long as they have a valid [Microsoft Account](https://www.microsoft.com/en-us/account).
8. If this user has a valid **Microsoft Account**, the system will validate it and it will be colored blue. Click on the blue user and confirm the entry by clicking on the **Select** button.

![1-2 Add new User and Select a role in DevTest Labs](/assets/images/2016/06/1-2-Add-new-User-and-Select-a-role-in-DevTest-Labs.jpg "1-2 Add new User and Select a role in DevTest Labs")

### Step 2: Add Owner in DevTest Labs 

**DevTest Labs** does not allow adding the **Owner** role at the lab level as this is not currently supported. To add the **Owner** role, you will have to add it in the **Subscriptions** of the lab. The **Owner** role has full access to all management and other functionalities in the lab.
1. Navigate to **Subscriptions** of the lab.
2. Choose the right **Subscription** from the list.
3. Navigate to **Settings**.
4. Click on **Users** to add a new user.
5. Click on the **Add** button.

![2-1 Add Owner in DevTest Labs](/assets/images/2016/06/2-1-Add-Owner-in-DevTest-Labs.jpg "2-1 Add Owner in DevTest Labs")

6. In the **Add access** blade, click on **Select a Role**.
7. In the **Select a role** blade, click on **Owner**.
8. In the **Add access** blade, click on **Add users**.
9. Type the **e-mail address** of the **Owner**.
10. If this user has a valid **Microsoft Account**, the system will validate it and it will be colored blue. Click on the blue user and confirm the entry by clicking on the **Select** button.

![2-2 Add Owner and select a role in DevTest Labs](/assets/images/2016/06/2-2-Add-Owner-and-select-a-role-in-DevTest-Labs.jpg "2-2 Add Owner and select a role in DevTest Labs")

### Conclusion

You can secure your lab by adding and defining different roles. It is important to know that the user who created the **VM** gets automatically assigned to the **Owner** role on the created **VM**. This user can then perform all the actions that are offered in the lab. However, the creation of **Virtual Machines** is only allowed from the **DevTest Labs account**.

>You can see this video, if you would like to find more information about how to create a Linux machine on Azure. We will select Ubuntu server and remote connect to it using Git Bash and PuTTY, and we will see how to test that our connection is established using the sudo command.
{: .prompt-tip }

{% include embed/youtube.html id='C0ecnvmdAuQ' %}
