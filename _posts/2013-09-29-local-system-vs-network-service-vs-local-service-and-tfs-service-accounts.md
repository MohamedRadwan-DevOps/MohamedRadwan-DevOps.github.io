---
layout: post
title: "Local System vs. Network Service vs. Local Service and TFS Service Accounts"
date: 2013-09-29 22:44:34 +0100
---

[TFS Service accounts](http://msdn.microsoft.com/library/ms253149.aspx "TFS Service accounts") are one of the very important topics when working with TFS installation and configuration. Each service needs to run with an account that might have different permissions. It is preferred to use different service accounts, but you can still use the same domain or workgroup account for all services, or you might use the system account like **Network Service**. An example of a reason for using **Network Service** is that you don’t need to worry about service interruption because of changing the password policy. However, as best practices and for better security reasons, we should use service accounts. To understand service accounts, let’s start from the beginning.

---

>For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see [Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/).
{: .prompt-tip }
{% include embed/youtube.html id='4DUhc0MjdUc' %}

---

**What are service accounts and why do we need them?**

To understand the answer, let’s think about why we need user accounts in the first place. We need user accounts so multiple users can log in to the system and have different privileges over the existing resources and applications, and also for network resources.

![Local System vs.Network Service vs. Local Service 2](/assets/images/2013/09/local-system-vs-network-service-vs-local-service-2-1.jpg?w=660)

What if I want to run an application or in other words a background process (**Service**) without needing any user to log in and without using any user account with their password?

![Local System vs.Network Service vs. Local Service 3](/assets/images/2013/09/local-system-vs-network-service-vs-local-service-3.jpg?w=660)
So we need to create user accounts for our services (**service accounts**). Does that mean I have to create them? No, there are some built-in user accounts without passwords that you can use directly. Each built-in account has different properties and purposes.

![Local System vs.Network Service vs. Local Service 5](/assets/images/2013/09/local-system-vs-network-service-vs-local-service-5.jpg?w=660)

**Local System:** The built-in **Local System** user account has no password and has a high level of access privileges; it is part of the Administrators group and presents the computer's credentials to remote servers.

**Network Service:** The built-in **Network Service** user account has fewer access privileges on the system than the **Local System** user account; it is part of the Users group but is still able to interact throughout the network with the credentials of the computer account.

**Local Service:** The built-in **Local Service** user account has fewer access privileges on the local computer; it is part of the Users group. Use the **Local Service** user account if the worker process does not require access outside the server on which it is running.

**So how can I configure the desired service to use Local System or Network Service accounts?**

Double-click on the service and in the **Log-On** tab choose **Local System** or just type browse and type **Network Service**.

![Assign Local System account to service](/assets/images/2013/09/assign-local-system-account-to-service.jpg)

![Assign Network Service to service](/assets/images/2013/09/local-system-vs-network-service-vs-local-service-6.jpg)

---

>For more information about how to work with **Docker**, such as pulling a docker image, running a docker image, and working with containers, see [Docker for beginners](https://mohamedradwan-devops.github.io/2019/05/31/docker-for-beginners-step-by-step-tutorial/).
{: .prompt-tip }
{% include embed/youtube.html id='3RJv6yVfaRE' %}

---

**So how can I grant permission for resources over the network for Network Service or Local System?**

On the other PC (PC-2), just grant permission to the first PC (PC-1) using the PC name + "\$" (PC-1\$).

![Local System vs.Network Service vs. Local Service 4](/assets/images/2013/09/local-system-vs-network-service-vs-local-service-4.jpg?w=660)

In summary, we have three different built-in accounts. Two of them can access the network and they are the same for network resources (**Network Service** - **Local System**), and two of them can access the local resources with least privileges (**Local Service** - **Network Service**).

![Local System vs.Network Service vs. Local Service 6](/assets/images/2013/09/local-system-vs-network-service-vs-local-service-6-1.jpg?w=660)