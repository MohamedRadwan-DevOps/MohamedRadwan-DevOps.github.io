---
layout: post
title: "Quick overview of Azure DevTest Labs"
date: 2016-06-29 16:34:36 +0100
---


### Introduction 

**[Azure DevTest Labs](https://azure.microsoft.com/en-us/services/devtest-lab/)** is a service that helps developers and testers quickly create environments in **Azure** while minimizing waste and controlling cost. In other words, it is also known as a self-service sandbox environment in **Azure** for quick creation of test environments while minimizing waste and controlling costs. Users can test the latest version of applications by provisioning **Windows** and **Linux** environments through reusable templates and **Artifacts**. **Azure DevTest Labs** allows users to easily integrate their deployment pipeline with **DevTest Labs** to provision on-demand environments. Users can scale up their load testing by provisioning multiple test agents and create pre-provisioned situations for training and demos. **Azure DevTest Labs** is a free service. However, you will be charged for other **Azure** resources that are created in the **Lab**. For example, you will be charged for the **[Virtual Machines](https://azure.microsoft.com/en-us/services/virtual-machines/)** that are created in the **DevTest Labs** in accordance with **Virtual Machine** pricing. More about pricing is available on [https://azure.microsoft.com/en-us/pricing/details/virtual-machines/.](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/.). The cost of **Virtual Machines** can be reduced with [Scheduled VM Shutdown with Azure Automation](https://mohamedradwan-devops.github.io/posts/microsoft-azure-scheduled-vm-shutdown-with-azure-automation/). The service is available in all 15 public regions that support the required **Azure** resources used in the **Labs**, including Australia, Brazil, and more regions in the United States, Europe, and Asia. This post will introduce the main advantages of using **Azure DevTest Labs** as a service for developers and testers, how it can help improve your team projects, and how to achieve very high quality without time-consuming tasks.

![1-Azure DevTest Labs](/assets/images/2016/06/1-Azure-DevTest-Labs.jpg "1-Azure DevTest Labs")

### Challenges in process of delivering the project 

Many developers and testers face numerous challenges in the process of delivering projects on time and with high quality. Using **Azure DevTest Labs** helps developers overcome challenges such as: time-consuming settings of environments, delays in delivering environments to developers/testers introduced by the traditional environment-request model, production devotion issues, and the high cost of cloud resource management to optimize resource usage.

![2-Azure DevTest Labs Challenges in process of delivering the project](/assets/images/2016/06/2-Azure-DevTest-Labs-Challenges-in-process-of-delivering-the-project.jpg "2-Azure DevTest Labs Challenges in process of delivering the project")

### Benefits of Azure DevTest Labs 

**Azure DevTest Labs** solves developers' problems by providing a self-service sandbox environment, which allows them to quickly create **DevTest** environments with minimal time-consuming tasks and control over costs.

- **Ready to test in just a few clicks:** **DevTest Labs** enables developers and testers to quickly create pre-provisioned environments with everything their team needs to develop and test the project. Depending on the project needs, you can start with base images from the **Azure Marketplace** or **Custom images** from your own **VHD**. Reusable artifacts are available to install tools, run **VM extensions**, deploy applications, or run other custom actions on demand once the **VM** is created. It enables you to have an environment with already installed builds in just a few clicks so that you can start on your project immediately.

- **Self-administration stress-free tool:** Developers and testers can provision their own environments without any unpredictable costs, which could cause high expenses. This is enabled because of **DevTest Labs** policies and **Azure Role-Based Access Control** (RBAC) model. Users can set many different policies for their own lab, such as the number of virtual machines per lab user and **VM** sizes allowed for **VM** creation. Developers can even create policies for automated shutdown of **Virtual Machines** based on a schedule or other criteria. For each policy, users can set thresholds and receive alerts.

- **One-time creation, unlimited usage anywhere:** **Azure Resource Manager templates** and **Artifacts** are designed to be shared with the team or even with other organizations. Custom images and formulas can be created for repetitive usage, including from existing **Virtual Machines**. Developers can use **Azure Resource Manager** templates to enable lab automation or environment provisioning. **Artifacts** loaded from source control repositories, such as **Visual Studio Team Services Git** or **GitHub** repositories, can be used across different labs.

- **Integration with existing toolchain:** Users can use predefined plug-ins or **Azure's API** to provision test environments directly from their preferred continuous integration (CI) tool, integrated development environment (IDE), or automated release pipeline. The service allows users to use their comprehensive command-line tool. In addition to **API's** and command-line tools, **Azure DevTest Labs Tasks** is available in **Visual Studio Marketplace** to better support your release pipeline in **Visual Studio Team Services**. There are three tasks that you can use to (respectively) create a **Lab VM** to run the tests, save the **VM** with the latest bits as a golden image, and delete the **VM** when it's no longer needed after the testing is done.

![3-Benefits of Azure DevTest Labs](/assets/images/2016/06/3-Benefits-of-Azure-DevTest-Labs.jpg)

### Conclusion

All contemporary **DevOps teams** are in constant search for different kinds of environments while implementing their software systems. It's very important that this environment is on time and well configured; otherwise, the team can face frustration and late deliveries. With **Azure DevTest Labs**, teams can access their environments in minutes instead of days or weeks. It is designed specifically for team usage on demand. It offers great support for all teams and will make teams more efficient and adjustable. The development of **Azure DevTest Labs** is an ongoing process. The output will continuously bring new supported types for **Azure** resources and adaptive policies.

>You can see this video, if you would like to find more information about how to install Visual Studio 2017 and point to some tricky components. See which Workloads need to be installed and which Individual Components need to be selected additionally. See how to install another Edition of Visual Studio and just put a different nickname in order to distinguish installed editions.
{: .prompt-tip }

{% include embed/youtube.html id='hDujfznIZFE' %}
