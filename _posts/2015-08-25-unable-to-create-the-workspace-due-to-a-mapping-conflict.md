---
layout: post
title: "Unable to create workspace due to a mapping conflict"
date: 2015-08-25 14:00:26 +0100
---

### It's a small issue, you may encounter if you name your build definition with the same name as an old one.

Here is the error Exception Message: Unable to create the workspace '80_6_tfs2bld' due to a mapping conflict. You may need to manually delete an old workspace. You can get a list of workspaces on a computer with the command 
`tf workspaces /computer:%COMPUTERNAME%`

```
Details: The path C:\Builds\6\Windows\src is already mapped in workspace 77_6_tfs2bld. (type MappingConflictException) 

Exception Stack Trace: 
at Microsoft.TeamFoundation.Build.Workflow.Activities.TfCreateWorkspace.Execute(CodeActivityContext 
at System.Activities.CodeActivity`1.InternalExecute(ActivityInstance instance, ActivityExecutor executor, BookmarkManager bookmarkManager) 
at System.Activities.Runtime.ActivityExecutor.ExecuteActivityWorkItem.ExecuteBody(ActivityExecutor executor,BookmarkManager bookmarkManager,
```

[![Unable to create the workspace due to a mapping conflict](/assets/img/2015/08/unable-to-create-the-workspace-due-to-a-mapping-conflict.png)](/assets/img/2015/08/unable-to-create-the-workspace-due-to-a-mapping-conflict.png)

If you would like to learn more about using the [Build Variables](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?tabs=batch) in [VSTS](https://www.visualstudio.com/team-services/) and Release Management, have a look at the following post: [VSTS Build variables and Echo](https://mohamedradwan-devops.github.io/posts/vsts-build-variables-and-echo/). The post describes how to see the output at any point of time, while automating a process, through setting variables and displaying them during the build.
{: .prompt-info }

You will need to go to the build machine, search for the old workspace that uses the same build definition name, delete that one so the build can create a new workspace with the same name again. 

![Delete workspace](/assets/img/2015/08/delete-workspaace.png)

### You can see **this video**

{% include embed/youtube.html id='uGAcWLnSU0A' %}

If you would like to find more information about how to get started with Release Management and its advantages. See how to create a build definition using CI/CD Tools for VSTS Extensions (I will be using Package Extension and Publish Artifact tasks), and also using DevOps-VSTS-POC trigger in order to enable CI, all of that in order to be able to publish, share, install and query versions.

You will see how to create a release definition, choose an artifact and configure the source for the artifact and default version. See how to create different environments or clone the existing one. In my case, I am going to create QA, Preproduction, and Production environments, each with one phase and one task. See also how to configure the Publish Extension task for each environment. See an end-to-end continuous delivery pipeline using VSTS extension with Build and Release Management.
