
---
layout: post
title: "Understanding TFS Process Customization in Details - Series"
date: 2014-02-16 02:27:34 +0100
---

Three years ago I wrote a blog post about [Customizing TFS Process 2010](https://mohamedradwan-devops.github.io/posts/customize-tfs-process-2010-video/ "Customizing TFS Process 2010"). This was a basic customization, but today I will deep dive with more details about **TFS Customization Process.** In this blog series, I will explain **TFS Process Customization** in detail. I will try to explain what happens behind the scenes, show common errors that occur when we perform customization, and answer many questions that could come up for anyone performing TFS Process Customization. This series consists of the following parts:

- [Part 1 - Working with Fields](https://mohamedradwan-devops.github.io/posts/understanding-tfs-process-customization-in-details-series/ "Part 1 - Working with Fields")
- [Part 2 - Understanding Action for state transition in Details](https://mohamedradwan-devops.github.io/posts/understanding-action-for-state-transation-in-details/ "Part 2 - Prepare SharePoint for the new system.")
- [Part 3 - Place Holder 2](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-2-prepare-sharepoint-for-the-new-system/ "Part 2 - Prepare SharePoint for the new system.")
- [Part 4 - Place Holder 3](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-2-prepare-sharepoint-for-the-new-system/ "Part 2 - Prepare SharePoint for the new system.")
- [Part 5 - Place Holder 4](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-2-prepare-sharepoint-for-the-new-system/ "Part 2 - Prepare SharePoint for the new system.")
- [Part 6 - Place Holder 5](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-2-prepare-sharepoint-for-the-new-system/ "Part 2 - Prepare SharePoint for the new system.")

Each part consists of one or many sections as needed.

## [Part 1 - Working with Fields]

I will start by introducing working with fields. There are many questions that come to mind when we start working with fields, such as:

- **Why do we need to create a field?**
- **What happens when we create a new field?**
- **Does the field exist per project or collection?**
- **Can we use the field multiple times for different work items?**
- **Can we have two fields with the same name or the same reference name?**
- **Can we change the data type of an existing field?**
- **Can we know which fields are not used anymore?**
- **If we delete a field from WID (Work Item Definition) or Global Workflow, is it deleted from our DB?**
- **Can we delete fields?**
- **If I remove a field from WID and it has data in the DB, and I return it back, do I get the data back?**
- **Can we enhance query speed using our new fields?**

First, here is the existing reference for all fields that come with TFS: [Work item field reference for Visual Studio ALM](http://msdn.microsoft.com/en-us/library/ms194971.aspx "Work item field reference for Visual Studio ALM")

- **Why do we need to create a field?**

This is a very important question because some people think that we create a field so we can add that field to the Work-Item form so the user can enter data for it. Yes, that\'s true, but also sometimes we create a field without needing to show it on the form. Maybe we will track some values in that field during the workflow or maybe during the form data changes, so not every field added will be added to the form.

- **What happens when we create a new field?**

We simply create a new field by opening [TFPT (Microsoft Visual Studio Team Foundation Server 2013 Power Tools)](http://visualstudiogallery.msdn.microsoft.com/f017b10c-02b4-4d6d-9845-58a06545627f "Microsoft Visual Studio Team Foundation Server 2013 Power Tools") Process Editor from Visual Studio and open a Work Item from file or from the server, go to **Fields** and click **New**. We will need to provide **Name** and **Reference Name,** and also choose a **Data Type** as well. 

![2-12-2014 3-34-53 PM](/assets/img/2014/02/2-12-2014-3-34-53-pm.jpg?)

We can also create fields by exporting **WID** (Work Item Definition), adding a new field, and then importing **WID** to the desired project, or by using **Global Workflow Definition**, or the GUI using Process Editor and clicking save.

As we can see in the following **WID** (Work Item Definition), it has 3 sections: **FIELDS**, **WORKFLOW**, and **FORM**. Adding a field will add this field to the **FIELDS** section with the FIELD element, and all rules will be inside that element.


```xml
<WORKITEMTYPE name="Product Backlog Item">
    <FIELDS>
        <FIELD name="Radwan Value3" refname="Radwan.Value3" type="String">
            <Rule1></Rule1>
            <Rule2></Rule2>
        </FIELD>
    </FIELDS>
    <WORKFLOW>
        .....
    </WORKFLOW>
    <FORM>
        .....
    </FORM>
</WORKITEMTYPE>

``` 

TFS will create that field inside **11 views** to track Work Items changes and updates for that field and, of course, other fields as well. This only happens for all data types except **PlainText** and **HTML** because they are not physical columns in the DB like the other fields. This is why we can only change data types between **PlainText** and **HTML** as we will see later on this post.

![2-12-2014 3-57-35 PM](/assets/img/2014/02/2-12-2014-3-57-35-pm.jpg)

These are the views affected by creating 2 fields:

![2-12-2014 1-55-56 PM](/assets/img/2014/02/2-12-2014-1-55-56-pm.jpg)

So let's see some of those views in more detail:

**View WorkItemChanges**  
It keeps all the records of the WI changes except (without) the last update. It shows under each field the last value if the field changed or NULL if the field did not change. In other words, it only shows values if this field changed in the last update, as seen in the following image.

![2-12-2014 1-52-02 PM](/assets/img/2014/02/2-12-2014-1-52-02-pm.jpg)

**View WorkItemsUpdate**  
It keeps the last record of the WI changes, as seen in the following image.

![2-12-2014 2-11-05 PM-2](/assets/img/2014/02/2-11-05-pm-2.jpg?)

**View WorkItemsLatestUsed**  
It keeps the last record of the WI changes.

**View WorkItemsAreUsed**  
It keeps the last record of the WI changes.

**View WorkItemsQueryEverable**  
It keeps all the records of the WI changes, including the last one.

![2-12-2014 1-47-29 PM-3](/assets/img/2014/02/2-12-2014-1-47-29-pm-3.jpg)

### Is the field per project or collection?

Fields are created per DB or TFS Collection. See the following image that illustrates the scope of different objects across TP and TP Collection.

![IC548825](/assets/img/2014/02/ic548825.png)

![2-12-2014 2-06-30 PM](/assets/img/2014/02/2-12-2014-2-06-30-pm.jpg)

So let's see some rules that you need to consider while creating a new field in TFS Work Item.

### Can we use a field multiple times for different work items?

You can add the same field for different Work Items as long as needed, but you need to use the same **Reference Name** and **Name** that you used the first time you created that field. TFS will understand that it is the same field you created earlier and will not create a new field. You can have different values for the following attributes for the same field inside different Work Items, such as:

- Label or the name that displays on the work item form
- The help text
- The allowed values within a drop-down menu

You can't have 2 fields with the same **Reference Name** per collection. If you try to save a field that already exists with the same **Reference Name** but with a different **Name**, TFS will warn you that you are trying to rename an existing field, as shown in the following error.

![2-12-2014 3-06-26 PM](/assets/img/2014/02/2-12-2014-3-06-26-pm.jpg)

Also, you can't have 2 fields with the same **Name** per collection. If you try to save a field that already exists with the same **Name** but with a different **Reference Name**, TFS will warn you that this **Name** is already used with an existing field or **Reference Name**, as shown in the following error.

![2-12-2014 3-20-52 PM](/assets/img/2014/02/2-12-2014-3-20-52-pm.jpg)

### Can we change the data type of an existing field?

If you add a field with a certain data type and save that field, you can't change its data type. If you try to do that, you will see the following error message.

![2-13-2014 11-34-45 AM](/assets/img/2014/02/2-13-2014-11-34-45-am.jpg)

You can only change the data type from **HTML** to **PlainText** or **PlainText** to **HTML**. You can't even use Process Editor (GUI) to do that; it is only available from the command line tool (**witadmin** **changefield**). We can also use that command to make the field synchronize with Active Directory in case that field stores names like created by, approved by, etc. Instead of just using static text, the text will sync with AD.

```powershell
witadmin changefield /collection:http://vsalm:8080/tfs/MyCollection /n:Radwan.Value1 /type:PlainText


- **Can we know which fields are not used anymore?**

We can use (**witadmin** **listfields**) to list all fields. This will show if the fields are used or not, and we can also use the option of (**/unused**) to only display fields that are not used.

### If we delete a field from WID (Work Item Definition) or Global Workflow, is it deleted from our DB?

### Can we delete fields?

### If I remove a field from WID and it has data in DB and return it back, do I get the data back?

Removing a field from **WID** or **Global Workflow** will not delete the field from the **DB** even if it does not have any data. We use (**witadmin** **deletefield**) to delete fields from the **DB**, but first, we need to make sure that this field is not used. We use (**witadmin listfields**) to know that and then remove that field from the form (**Layout**) if it exists and then remove it from the field list in the **WID**. If we remove the field from **WID** without deleting it using (**witadmin** **deletefield**), then we can return it back as all data are still there in the DB and linked to **WI** by **ID**.

**Remember:** If you delete a field, you will need to [**rebuild TFS Data warehouse**](http://msdn.microsoft.com/en-us/library/cc668753.aspx "rebuild TFS Data warehouse") to update the reports by removing its value.

### Can we enhance query speed using our new fields?

We have a command (**witadmin** **indexfield**) we can use to index our field, which can increase query speed using this field.

**Links:**

- [Work Item Field Attributes - What You Can and Canot Change](http://blogs.msdn.com/b/visualstudioalm/archive/2012/08/17/work-item-field-attributes-what-you-can-and-can-t-change.aspx "Work Item Field Attributes - What You Can and Can't Change")
- [Everything about TFS2013 customization](https://www.simple-talk.com/dotnet/visual-studio/customizing-team-foundation-server-2013/)
