---
layout: post
title: "Fix Build-Deploy-Test workflow error, There are no test cases matching the criteria specified"
date: 2014-05-26 11:51:40 +0100
---

You may face the following error while you are running your Build-Deploy-Test workflow: 

> Exception Message: There are no test cases matching the criteria specified. Use Microsoft Test Manager to view the test cases. 
{: .prompt-danger }

This could happen for many reasons:

1. **You didn't select the test suites that include your test cases**:
   Make sure you select the correct test suites, see the following image:
   
   ![Test Suites Selection](/assets/img/2014/05/2014-05-26_12-42-06.jpg)

2. **You chose the wrong configuration**:
   Ensure you select the right configuration that matches the one existing in the test plan, see the following images:
   
   ![Configuration Selection](/assets/img/2014/05/2014-05-26_12-43-00.png)
   
   ![Configuration Details](/assets/img/2014/05/2014-05-26_12-44-23.png)

If you want to change the configuration for the test plan, follow these steps:

1. Open your test plan, select your test suite, and select all your test cases that you want to change their configuration.
   
   ![Select Test Suite](/assets/img/2014/05/2014-05-26_12-45-00.png)

2. Click on **configuration** and change the configuration.
   
   ![Change Configuration](/assets/img/2014/05/2014-05-26_12-45-32.png)
