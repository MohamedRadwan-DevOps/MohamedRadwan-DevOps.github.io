---
layout: post
title: "Hello world TFS SDK"
date:   2011-08-02 13:42:53 +0100
---

First, this was a very easy task, but it was my first task with the TFS SDK and WIQL (Work Item Query Language). In this post, I will create and retrieve work items using the TFS API and WIQL.

To retrieve work items like tasks, we will use the following code snippet:

```csharp
public void RetrieveWorkItems() 
{
    var tfs = TfsTeamProjectCollectionFactory.GetTeamProjectCollection(new Uri("http://TFS2011:8080/TFS/DefaultCollection"));
    var workItemStore = tfs.GetService<WorkItemStore>();
    var wiqlQuery = String.Format(
        @"Select [State], [Title] From WorkItems 
          Where [Work Item Type] = 'Task' 
          Order By [State] Asc, [Changed Date] Desc");
    WorkItemCollection witCollection = workItemStore.Query(wiqlQuery);

    foreach (WorkItem workItem in witCollection) 
    {
        Console.WriteLine("ID: {0}", workItem.Id);
        Console.WriteLine("Title: {0}", workItem.Title);
    }
}
```
To create work items like tasks, we will use the following code snippet:

```csharp
public void CreateTask() 
{
    var tfs = TfsTeamProjectCollectionFactory.GetTeamProjectCollection(new Uri("http://TFS2011:8080/TFS/DefaultCollection"));
    var workItemStore = tfs.GetService<WorkItemStore>();
    Project proj = workItemStore.Projects["SimpleTry"];
    WorkItemType type = proj.WorkItemTypes["Task"];
    WorkItem workItem = new WorkItem(type);
    workItem.Title = "Task entered using API";
    workItem["Activity"] = "Configuration";
    workItem.Save();
}

```

Remember you will need to add references to the following assemblies:

- [Microsoft.TeamFoundation.WorkItemTracking.Client]
- [Microsoft.TeamFoundation.Client]


For more information on how to use the TFS SDK, click [here](http://msdn.microsoft.com/en-us/library/bb130146(v=VS.80).aspx).

For more information on how to use WIQL (Work Item Query Language), click [here](http://msdn.microsoft.com/en-us/library/bb130319(v=vs.80).aspx).

For more information, click [here](http://msdn.microsoft.com/en-us/library/bb130322.aspx).