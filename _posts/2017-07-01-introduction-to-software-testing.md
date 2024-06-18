---
layout: post
title: "Introduction to software testing"
date:   2017-07-01 16:27:26 +0100
---

## Introduction 

Software testing represents the process of application examination in order to assure that application or project is meeting all the requirements and quality expectations for which was designed for. In this process testers will try to find the **Bugs**, using different scenarios. It\'s important from many aspects, but from most important one is to measure the **quality of the software**. In software development process, it\'s very important to understand what are the possible risks for certain software implementation. There are many advantages for software development with software testing, such as: **reducing the cost** of development and the **total cost of ownership**, as well as ensuring **proper behavior** for the end-user and developing customer loyalty.

### So, the main purpose of a testing job is **to identify and report out software bugs**

which are then in later phases reviewed and prioritized in the process known also as **Triage**. In **Triage**++the bugs will be separated, selected and sorted and on **Triage** meetings sometimes also happens that team decides to raise the triage criteria bar, which means that some of the reported bugs will remain unfixed. Remain unfixed bugs are representing a++**trade-off** meaning that these bugs are less important due to the time limitations, budget or meeting the project scope. After the bug is fixed, It\'s usually assigned back to the tester to verify it. Verification here means that tester will try to reproduce the bug and search for additional errors. Here it\'s very important to highlight the understanding of the **Bug States**, which are: **Active, Closed**, and **Resolved**. The meaning of **Active state** is clear and it means that bug is in process of investigation or fix. **Closed state** means that someone has verified that bug is fixed, but not everyone in team agreed or confirmed it. **Resolved state** implies that bug is fixed and that fix is verified. Before understanding the purpose of testing, it\'s also very important to understand the difference between software development methodologies which are used for management of those projects. They are divided into two main groups of development:

### Sequential and Iterative

[More Info]{.ion-info}To learn more about Agile Software Testing, have a look at the [quick guide about Agile Software Testing](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-agile-software-testing/). This guide presents the basic idea behind Agile methodology and its connection to software testing. It describes the structural idea of Agile and explains the importance of adaptation to changes in the fast-paced software development world.

**Sequential development** basically uses the waterfall method, which courses through a set of phases. In waterfall model of development, the team will finish each phase, before continuing with the next one. It requires a lot of organization and planning upfront and it\'s appropriate for big projects. **Iterative model** of development uses a short 2-3 week long sprints to finish a small portion of a project and then moves to next portion and so on. This model is incremental, delivers quickly, responds to changes and aims to get user feedback for each iteration. This model is using **Agile methodology**. 

![1-waterfall-vs-agile software dev test](/assets/images/2016/12/1-Waterfall-vs-Agile-1-1.jpg "1-waterfall-vs-agile software dev test")

## Software Testing Process

**Software Testing Process** differs by used methodology, testing level and between organizations, but it will generally remain the same either the team is using Waterfall method or working by [Agile](http://agilemanifesto.org/). The process can be slightly different between different organizations. [Software Testing](https://msdn.microsoft.com/en-us/library/cc188960.aspx) is the whole process and doesn\'t represent just one activity that needs to be implemented. Each step of the process requires certain activities that should be followed in order to get the best results. 

![2-software-testing-process](/assets/images/2016/12/2-Software-Testing-Process.png "2-software-testing-process")

The same testing process can be applied to all levels of testing, considering internal modifications to fit into the certain level.

## Manual vs Automated software testing

In [**Manual testing**](https://msdn.microsoft.com/en-us/library/dd380763(v=vs.110).aspx), the tester will play the role of a user and will seek for any unpredictable or unwanted behavior in the application or project. Of course, the tester will not just look for any bug, he will perform the tests in accordance with the test plan. Which will have specified test cases. Here it\'s also important to mention that every test case should include Test Case ID or Number. Summary, any Related Requirements, Prerequisites, Procedure or the steps, Expected and Actual Result. Status showing if test failed or succeeded, notes, data about who created the test and when who executed the test. And when and also the information about Test Environment showing which OS and browser were used.

You can see [this video](https://www.youtube.com/watch?v=tfWCYXxeTmc) if you would like to find more information about how to integrate automated UI tests with Visual Studio build automation in order to be able to integrate with Continuous Integration & Continuous Delivery Pipeline. First, you need to add test category and rebuild the application. Note that the build should be configured as a process. Not as a service in order to be able to run the automation UI. Afterwards I am going to commit EasyRepo UI Automation framework in Team Explorer. Changes in order to committed and synchronize the changes in my local EasyRepo on VSTS. See how to create new build definition using .NET Desktop template, remove unnecessary tasks as Publish symbols path, Copy Files to and Publish Artifact drop, but keep the Use NuGet, NuGet restore, Build solution, VsTest - testAssemblies tasks. How to set the correct Test filter criteria, and Test assemblies.

### Additionally learn how to use VSTest. 

Console.exe in order to run the automation form from command line and to debug the failing test. So, manual testing is conducted in accordance with the test case, which should be very well-defined and scoped.

On the other side, the [**Automated testing**](https://msdn.microsoft.com/en-us/library/dd380755(v=vs.110).aspx) means that test will be performed by a computer and as a set of already predefined steps. Automated tests can be created and build in a way that they will run each time when a part of source code will be changed. Using the Automated tests allows you to run the tests unattended, to use fewer resources and to have more stability as there are no human errors present. Also, they are reducing the effort and spent time, they can have higher coverage and they are handling those repetitive and maybe even boring tasks. Both types of testing are very important. But it\'s important to note that **Manual testing** will take longer time for execution. But it doesn\'t require long set-up time as **Automated testing** does. Therefore **Manual tests** are good to use where they need to be run. From time to time or in cases when the cost of setting up the automation would exceed the desirable one and there would be no value of it.

>If you would like to know more about this new developer service available on the [Azure](https://azure.microsoft.com/en-gb/) platform, you can have a look at the following post; [More about Azure DevTest Labs](https://mohamedradwan-devops.github.io/posts/more-about-azure-devtest-labs/). If you prefer a more concise description of the same feature, - [have a look at Quick overview of Azure DevTest Labs](https://mohamedradwan-devops.github.io/posts/quick-overview-of-azure-devtest-labs/).
{: .prompt-tip }

## Software Testing Levels and Types

Levels of testing are defined by given environment and requirements. Every level of testing includes different methodology which can be used during software testing process. ++In general, testing levels are divided into two main groups: **Functional and Non-functional testing**. [**Functional testing**](https://msdn.microsoft.com/en-us/library/ee290766(v=bts.10).aspx) is a category of black-box testing, which is simulating the end-user experience. It means that tester will play a role of a user. Which is not familiar with any background, for example how the code is working. Under Functional tests, there are many types of tests, such as Smoke testing, Regression testing, Usability testing . **Non-Functional testing** represents a testing of a software for its non-functional elements.++ Such as how many people can log in the same time. Testing the application performance requirement and other non-functional characteristics of software systems. Some of the test types under Non-Functional testing are Performance Testing, Load Testing, Security Testing, Maintainability Testing, Endurance testing, etc.

## Teams and communication in software testing

In software, testing communication is very important. It\'s also very important part of the whole development project. Models with **Agile development** depend on frequent or daily meetings. As communication is one of the key factors for the success of the project. Today\'s very common practice is to have [**Distributed teams**](https://msdn.microsoft.com/en-us/library/jj620910(v=vs.120).aspx). When having **Distributed teams.** The communication can be more difficult than having a team on the same locations. Having **Distributed team** has quite some advantages. Such as cost advantages due to less expensive resources having a deeper pool of talents and reach of the new markets. However, dealing with **Distributed** team has also some disadvantages, especially in communication, as there can be quite some technical issues with sound or image. There are many great tools that distributed teams are using for communication, such as

[Skype](https://www.skype.com/en/), 
[Share Point](https://products.office.com/en-us/sharepoint/collaboration), and 
[Yammer](https://www.yammer.com/).

>If you would like to learn more about Hockey App as it\'s part of Microsoft\'s Mobile DevOps stack helping developers manage the app lifecycle and automate integration, testing, delivery, and monitoring. Mobile Center is a new base for all of your mobile application needs. It is a set of DevOps tools including continuous integration, automated UI testing, distribution, crashes and analytics. You can use any number of these features independently, but the more you combine, the more powerful Mobile Center becomes. - have a look at this post - have a look at the [**this post**](%20https://mohamedradwan-devops.github.io/posts/the-next-generation-of-hockey-app-visual-studio-mobile-center-now-visual-studio-app-center/)
{: .prompt-tip }

## Conclusion

Software testing is an important part of **SDLC** ([Software Development Life Cycle](https://msdn.microsoft.com/en-us/library/jj159342.aspx)). The main purpose of software testing is to find errors. In any part of software already in early stages of software development. In order to assure the high level of quality. Releases of software with bugs and many errors can very negative consequences on the user experience and quality. **Testing environment** should be as much as possible similar to the production environment. So that testing results can show credible results and data.
