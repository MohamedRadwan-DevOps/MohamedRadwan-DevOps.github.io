---
layout: post
title: "Create a TFS Build Custom Activity to Read From File"
date: 2015-01-29 10:59:10 +0100
---

I needed to create a Custom Activity that reads from an XML file and displays the values on the Build log. It's very easy and I will not re-write how to do the basic Custom Activity, but if you are not familiar with that, you can see the following link: [Use and develop custom build process activities](https://msdn.microsoft.com/en-us/library/hh850441.aspx "Use and develop custom build process activities")

Here, I needed to add **OutArgument** to return the value that I got from reading the file. I will get the value from the file and assign that value to **OutArgument**.  

![OutArguemnt in TFS Custom activity](/assets/img/2015/01/outarguemnt-in-tfs-custom-activity.png)

After that, I built the project and distributed the library (DLL) under source control where the build controller points for the custom assemblies. See the previous link for the MSDN on how to do that. Open your process template that you want to use the new custom activity and right-click on the Toolbox and browse to the created library as the following image.  
![Add custom activity for The Visual Studio Toolbox](/assets/img/2015/01/add-custom-activity-for-the-visual-studio-toolbox1.png)

Drag and drop your new custom activity, declare a new variable (MyValue) to hold the return value from the reading process as the following image.  

![ReadFromXML Activity](/assets/img/2015/01/readfromxml-activity.png)

The Build summary will be as the following image. 

![Build Summary](/assets/img/2015/01/build-summary.png)

The build log will be as the following image.  

![Build Log](/assets/img/2015/01/build-log.png)

### Make the activity return a list of strings

We will need to define **OutArgument** as a `<List<string>>` and assign that in the execute method.  

![OutArgument as list of string](/assets/img/2015/01/outargument-as-list-of-string.png)

Declare a variable (MyValue) but this time the type is a `<List<string>>` too. Drag and drop a [For each] Activity of string and print each item in the list as follows: 

![ReadFromXML Activity for list of string](/assets/img/2015/01/readfromxml-activity-for-list-of-string.png)

The Build summary will be as the following image. 

![Build Summary for list of string](/assets/img/2015/01/build-summary-for-list-of-string.png)
