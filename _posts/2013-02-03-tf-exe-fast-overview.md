---
layout: post
title: "TF.exe Fast Overview"
date: 2013-02-03 11:15:34 +0100
---

In this post, I will give a fast overview of the tf.exe command line. I will show how to use different options, like checkin, workspaces, view, diff, status, and workfold. The most important consideration is to navigate to the mapping folder inside the working machine so we can use different options; otherwise, we will see the following error:

> [Unable to determine the workspace. You may be able to correct this by running]['tf workspaces /collection:TeamProjectCollectionUrl'].
{: .prompt-danger }

The following is a step-by-step video for the post: 

{% include embed/youtube.html id='7HjNb8oq1eY' %}

Open the Visual Studio Command Prompt as Administrator, and type ***tf msdn***. This will display the help.

![Open-VS-Command-Line](/assets/img/2013/02/open-vs-command-line-1.jpg)

![TF-msdn](/assets/img/2013/02/tf-msdn.jpg)

Type ***tf help checkin*** to display the help for the checkin option.

![Display-help-about-option](/assets/img/2013/02/display-help-about-option.jpg)

We will go to the project settings and add 2 notes: Reviewer and Time. After that, we will get back to the command line and type:

```bash
tf checkin /comment:"Hello this is my comment" /notes:"Reviewer=M.Radwan;Time=5:00"
```

![TF-Checkin-with-comment-notes](/assets/img/2013/02/tf-checkin-with-comment-notes-1.jpg)

This will display the checkin dialog-box with the typed comments and
notes.

[TF-Comment](/assets/img/2013/02/tf-comment-1.jpg)

![TF-Notes](/assets/img/2013/02/tf-notes.jpg)


Now we will output the different between 2 changeset in a file, type

```bash
tf diff FabrikamFiber.CallCenterfabrikamfiber.webcontrollers /version: c7\~c26 \>c:Radwan.txt
```

![TF-output-diff-in-file](/assets/img/2013/02/tf-output-diff-in-file.jpg)

Open the file using

[Notepad2](http://www.flos-freeware.ch/notepad2.html "Notepad2")

and select the **Diff Files** schema (Into ALM withTFS)


![TF-Open-diff-with-notepad2](/assets/img/2013/02/tf-open-diff-with-notepad2.jpg)

![TF-diff](/assets/img/2013/02/tf-diff-1.jpg)

To view a file a specific version type 

```bash
tfview FabrikamFiber.CallCenterfabrikamfiber.webcontrollersCustomerControllers.cs
/version:c26 
```

![TF-view](/assets/img/2013/02/tf-view.jpg)


