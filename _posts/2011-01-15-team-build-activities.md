---
layout: post
title:  "3-Team Build Activities part 1"
date:   2010-01-15 07:40:05 +0100
---

Today I will start introduce some of the important activities in the Team build 2010 as the following picture \

![Activities Toolbox](/assets/img/2010/11/Scope.jpg)

So this process has 3 main steps as the following:

![ Build Process main task](/assets/img/2010/11/Intro.png)

- GetBuildDetail Activity

This activity will return the Build Detail object which hold all information needed about the build, you need to declare a variable of type IBuildDetail to hold the object when return 

![BuildDetail](/assets/img/2010/11/GetBuildDetail.png)

If we print the BuildDetail variable .ToString we will find the following information, remember you can retrieve any info you find in the ToString from the BuildDetail as needed 

![BuildDetail.ToString](/assets/img/2010/11/GetBuildDetaiToStringl.png)

- AgentScope Activity

This activity used to group all activities that need to run on the Build Agent

- GetBuildAgent Activity

This activity must run on the Agent and inside AgentScope Activity, it will return the Build Agent object which hold all information needed about the Agent, you need to declare a variable of type IBuildAgent to hold the object when return

- GetBuildDirectory Activity

This activity must run on the Agent and inside AgentScope Activity, it will return string of the path of the build directory Notice that the variable Run on Agent in the picture because you must run them in the
Agent 

![](/assets/img/2010/11/GetBuildAgentAndBuildDirectory.png)

Notice that if we print the BuildAgent variable and BuildDirectory variable you will find all information needed for Agent and directory 

![AgentScope and insiders](/assets/img/2010/11/Print-GetBuildAgentAndBuildDirectory.png)

![BuildAgent and BuildDirectory](/assets/img/2010/11/BuildAgentAndDirectory.png)

- Assign Activity

This activity used to assign a string variable a value

- AddToCollection Activity

This activity used to add item to collection you can use it with the ForEach Activity to add the item in a collection for each iteration

- FindMatchingFiles

This Activity will find the files with specified pattern and return them as collection of IEnumrable\<String\>

- InvokeForReason Activity

This Activity will invoke based on the build trigger remember this trigger is flag enumeration which mean you can choose more than one option for invoke

![Other activities](/assets/img/2010/11/AssignAddCollectionFindMatch.png)

![MatchFile Pattern](/assets/img/2010/11/MatchFilePattren.jpg)

Finaly I will print out all the variables and I will use ForEach Activity to iterate over the collection that hold matches files to print all files 

![Print the variables](/assets/img/2010/11/PrintLastActivities.png)

The value will be as the following:

![The value of the print](/assets/img/2010/11/RunningTheProcess.png)

Remember BuildSettings and AgentSetting which will display the option the process definition

![BuildSettings AgentSettings](/assets/img/2010/11/ArgumentBuildSettings-AgentSettings.png)

Finished, wait me for Activities part 2 You can download the process from the following

[![Download](/assets/img/2017/08/XAML-icon.jpg)](/assets/img/2017/08/Radwan_Activites_Part1.zip)


