---
layout: post
title: "TFS Counter Command Line Tool"
date: 2015-07-15 16:03:55 +0100
---

I created a command line tool that provides a CSV file that counts all items for all projects in a TFS collection, like Count of ChangeSets, Count of Changes, Count of Files, Count of WorkItems, and Count of History of WorkItems. This tool might help you estimate the size of the project to migrate or move the project between servers or collections. [Download the tool from Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/f25cd380-7d2b-4aa1-b0d7-b10156702dc9)

![TFSCounter](/assets/images/2015/07/tfscounter.png)

> In one of the old posts [TFS 2015 Agile Project Management](https://mohamedradwan-devops.github.io/posts/tfs-2015-agile-project-management/) you can read more about new [**Agile Project Management**](https://docs.microsoft.com/en-us/vsts/work/backlogs/overview) features in **TFS 2015**, which provide better support for aligning across teams while giving autonomy to individual teams; you can use the same structure with VSTS/TFS2018.
{: .prompt-info }

The output of the CSV file will be like the following:
![TFSCountOutput](/assets/images/2015/07/tfscountoutput.png)

You can see the following video, if you would like to find more about how to start creating the VSTS package, which means putting all the files into one file so we are able to upload the VSTS extension. For that purpose, I am going to use TFS CLI (Command Line Interface), which is a cross-platform command line tool. Using this tool, I am going to put all my files into one file with extension vsix. First, I am going to download it using the node package manager, executing the `npm I -g tfx-cli` command. In order to put all files into the vsix package, I am going to run cmd from the application location and execute the following command `tfx extension create -manifest-globs vss-extension.json`.

{% include embed/youtube.html id='i2LzbISRLiU' %}
