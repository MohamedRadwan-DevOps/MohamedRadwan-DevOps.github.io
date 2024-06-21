---
layout: post
title: "Understanding Action for state transition in Details"
date: 2014-03-24 00:47:37 +0100
---

In this blog series, I will explain **TFS Process Customization** in detail. I will try to explain what happens behind the scenes, show common errors that occur during customization, and answer many questions that may arise for anyone performing TFS Process Customization. This series consists of the following parts:

- [Part 1 - Working with Fields](https://mohamedradwan-devops.github.io/posts/understanding-tfs-process-customization-in-details-series/ "Part 1 - Working with Fields")
- [Part 2 - Understanding Action for state transition in Details](https://mohamedradwan-devops.github.io/posts/understanding-action-for-state-transation-in-details/ "Part 2 - Prepare SharePoint for the new system.")
- [Part 3 - Place Holder 2](# "Part 3 - Prepare the new machine and install SQL Server.")
- [Part 4 - Place Holder 3](# "Part 4 - Install TFS 2012 Update 1 & Backup DBs and Reporting Key.")
- [Part 5 - Place Holder 4](# "Part 5 - Restore DBs and Reporting Encryption Key.")
- [Part 6 - Place Holder 5](# "Part 6 - Configure TFS 2012.")

Each part consists of one or many sections as needed.


### [Part 2 - Understanding Action for state transition in Details]{style="color:#339966;"}

{% include embed/youtube.html id='3eqXzAJ0ri4' %}

Action is a very confusing concept for many people. What is action? Can I create a custom action? How to use action or custom action? So, in this post, I will try to simplify what is really meant by Action and how it works.

**What is Action?**

It's just a unique string that is used as a flag that is added in the transition between states to be used by third-party tools. This way, we can know which is the current state and which is the next state for a given action in a work item.

Imagine that I have created a small application that has only one button that lists some work items from different types of work items (Bug, Task, Change Request, etc).

![Change Sate based on action transation](/assets/img/2014/03/change-sate-based-on-action-transation.png)

I want when I click on the button, all work items from **Type-1** change from **State-1 to State-2**. If the work items are in **State-2 or State-3**, it remains in the same state. I also need all work items from **Type-2** to change from **State-2 to State-3**, but if the work items are in **State-1 or State-3**, it remains in the same state.

To do that, I need to go to the WID (Work Item Definition) for these two types of work items and in the transition between the desired states, I will put my custom action, and this action can be retrieved by TFS SDK afterward.

**Work-item type 1**

```xml
<TRANSITION from="State-1" to="State-2">
  <ACTIONS>
    <ACTION value="Radwan.Actions.CustomAction"/>
  </ACTIONS>
</TRANSITION>
```
![Action](/assets/img/2014/03/action.jpg)

**Work-item type 2**

```xml
<TRANSITION from="State-2" to="State-3">
  <ACTIONS>
    <ACTION value="Radwan.Actions.CustomAction"/>
  </ACTIONS>
</TRANSITION>

```

![Action-2](/assets/img/2014/03/action-2.jpg)

So when I get the next state using TFS API or (SDK) with this custom action, I can know which work item is in the desired state, so I can advance it to the next state. If the work item doesn't have the action in the transition, it means I don't need to advance its state.

The following code gets some work items, iterates over them, gets the next state for my custom action, and prints the next state if it finds that action.

```csharp
WorkItemCollection witCollection = workItemStore.Query(wiqlQuery);
foreach (WorkItem workItem in witCollection)
{
    Console.WriteLine("Next State for {0} is {1}", workItem.Title, workItem.GetNextState("Radwan.Actions.CustomAction"));
}

```
This will tell me if my flag (Custom Action) is there or not and what is the next state so I can advance (change) the state.

```csharp
class Program
{
    static void Main(string[] args)
    {
        RetrieveWorkItems();
        Console.Read();
    }

    public static void RetrieveWorkItems()
    {
        var tfs = TfsTeamProjectCollectionFactory.GetTeamProjectCollection(new Uri("http://VSALM:8080/TFS/Collection"));
        var workItemStore = tfs.GetService<WorkItemStore>();
        var wiqlQuery = String.Format(@"Select [State], [Title] From WorkItems Where [Work Item Type] = 'Task' Order By [State] Asc, [Changed Date] Desc");

        WorkItemCollection witCollection = workItemStore.Query(wiqlQuery);
        foreach (WorkItem workItem in witCollection)
        {
            Console.WriteLine("ID: {0}", workItem.Id);
            Console.WriteLine("Title: {0}", workItem.Title);
            Console.WriteLine("Next State for {0} is {1}", workItem.Title, workItem.GetNextState("Microsoft.VSTS.Actions.Checkin"));
            Console.WriteLine("Next State for {0} is {1}", workItem.Title, workItem.GetNextState("Radwan.Actions.CustomAction"));
            Console.WriteLine("");
        }
    }
}

```

### Links:

[Automate field assignments based on State, Transition, or Reason](http://msdn.microsoft.com/en-us/library/ms194990.aspx)
[Work item Action lis](http://social.msdn.microsoft.com/Forums/vstudio/pt-BR/4f40db2f-3440-4965-884d-dd915fdc03bc/work-item-action-list?forum=tfsworkitemtracking)

[Obtain possible next states of a work item programatically?](http://social.msdn.microsoft.com/Forums/vstudio/en-US/48a70325-d2b6-4e53-b1c5-8d08f68fb34b/obtain-possible-next-states-of-a-work-item-programatically?forum=tfsworkitemtracking)
[Changing State according to a field\'s value](http://social.msdn.microsoft.com/Forums/vstudio/en-US/0ce431bc-a8ee-44b1-9388-ca82bc2d9689/changing-state-according-to-a-fields-value?forum=tfsworkitemtracking)
[New State for TFS 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/03/06/get-your-agile-project-fixed-after-an-upgrade-from-tfs2010-to-tfs11-beta.aspx)
[WorkItem.GetNextState Method](http://msdn.microsoft.com/en-us/library/microsoft.teamfoundation.workitemtracking.client.workitem.getnextstate.aspx)


