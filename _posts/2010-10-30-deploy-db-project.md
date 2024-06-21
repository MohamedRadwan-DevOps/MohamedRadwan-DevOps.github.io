---
layout: post
title:  "Deploy DB project with Team Build 2010"
date:   2010-10-30 07:40:05 +0100
---

I work in a project and I try to automate everything so I just need to automate the deployment of the project including the DB with the CI (continuous integration) to QA machine or Testing environment so the scenario start with the developer try to check-in his code so the team build start build the project and when he succeeded it will deploy the website to the Testing web server and deploy the DB to the Testing DB server, to keep my article simple I will just describe the part of the DB only so I will separate it from the rest of the project

1.  Create DB project
    
    ![Edit DB properties](/assets/img/2010/10/DBProperties.jpg)

<!-- -->

2.  Edit the properties of the DB project in the deployment tab so it
    will deploy script and create the DB 
    
    ![Edit deploy tab](/assets/img/2010/10/DeployDBOption.png)

3.  Check-out any process template from the process template folder
    
    ![Check-out process](/assets/img/2010/10/Check-inProcess.png)

4.  Copy the file an rename it to the name you want
   
5.  Add the file to the source control and check-in it after rename it
    
    ![Add the process to the source control](/assets/img/2010/10/AddProcess.png)

6.  open the new file
   
7.  Delete all steps, arguments and variables 
   
   ![Delete any items](/assets/img/2010/10/DesingProcess.png)

8.  Add sequence task and a MS Build task inside the sequence from the
    tool box 
    
    ![Add Sequence and MS build tasks](/assets/img/2010/10/MSBuildProperties.png)
    

9.  Start adding the following argument as the following image 
    
    ![Arguments](/assets/img/2010/10/MSBuildProperties2.jpg)
    
    ![Arguments 2](/assets/img/2010/10/MakeArgumentWithTargets.png)

    ![Set Configuration](/assets/img/2010/10/PassArgument.png)

10.  Save the file
    
11. Check-in the file
    
12. To keep my article simple I will do this step manually, copy your DB
    project folder to the Team Build machine folder

13. Start create new build definition from the new process file and give this build definition the need parameter and one of them is the path of the DB project on the Team build server
    
    ![New build definition](/assets/img/2010/10/New-Build-Defination.png)
    
    ![Build use the create process](/assets/img/2010/10/AddyourTemplate.png)
    
    ![Put the build parameters](/assets/img/2010/10/BuildDefinationWithVariable.png)

14. Queue and build using the created build definition

15. check your DB.

16. Done.

You can download the process template files and the parameters value by clicking [here](http://cid-4bcaa16d27b46600.office.live.com/self.aspx/.Public/Blog%20New/MSBuild/Deploy%20DB%20from%20Team%20Build/Process%20templates%20and%20parameters.zip "Download the process template")