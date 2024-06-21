---
layout: post
title: "TFS Update 4 CTP 2 Features and installation"
date: 2014-10-13 08:52:21 +0100
---

Microsoft released Visual Studio 2013 Update 4 Community Technology Preview 2 (CTP 2) on September 22, 2014. It includes some new features and bug fixes. For more information about this release visit the KB: <https://support2.microsoft.com/kb/2994375>

This post has two main sections:

## Team Foundation Server Features

- Web Access can return directly to query results from a detailed view of the query by using a context menu.
- Web Access can generate an email directly from the work item view by using a new toolbar command.
- Web Access has a full-screen option to view query results.
- The free Stakeholder license provides access to the project home page from which Stakeholders can view the backlog, edit items, run work item queries, and many other operations.
- Agile teams can have up to 999 work items in the first or last column of the Kanban board.
- Web Access now opens a work item in a new window or tab.
- You can maximize (or full screen) fields for quick readability when the rich text editor does not have enough space.

## Installation and Configuration

- What you need to know before you install
- How to install and configure.

### Team Foundation Server Features

The following is the walkthrough video:

{% include embed/youtube.html id='gByYtNfo26g' %}

#### Web Access can return directly to query results from a detailed view of the query by using a context menu.

In Team Web Access, if you run a query and open a work item from the query result, you can get back to the query result from the work item context menu on the top-right.

![9-25-2014 5-56-27 PM](/assets/img/2014/10/9-25-2014-5-56-27-pm.png)

![9-25-2014 5-58-17 PM](/assets/img/2014/10/9-25-2014-5-58-17-pm.png)

#### Web Access can generate an email directly from the work item view by using a new toolbar command.

In the previous update 3, you could send an email from the context menu only, but now you can send an email from the work item toolbar.

[![image005](/assets/img/2014/10/image005.png)](/assets/img/2014/10/image005.png)

![9-25-2014 6-29-13 PM](/assets/img/2014/10/9-25-2014-6-29-13-pm.png)

#### Web Access has a full-screen option to view query results.

Now you can full-screen the query result for better readability.

![9-25-2014 6-32-19 PM](/assets/img/2014/10/9-25-2014-6-32-19-pm.png)

[![image011](/assets/img/2014/10/image011.png)](/assets/img/2014/10/image011.png)

#### The free Stakeholder license provides access to the project home page from which Stakeholders can view the backlog, edit items, run work item queries, and many other operations.

There is a new Access level feature for the Stakeholder that gives them more features than the limited level.

![9-25-2014 6-35-07 PM](/assets/img/2014/10/9-25-2014-6-35-07-pm.png)

#### Agile teams can have up to 999 work items in the first or last column of the Kanban board.

![9-25-2014 6-37-38 PM](/assets/img/2014/10/9-25-2014-6-37-38-pm.png)
#### Web Access now opens a work item in a new window or tab.

![9-25-2014 8-50-03 PM](/assets/img/2014/10/9-25-2014-8-50-03-pm.png)

#### You can maximize (or full screen) fields for quick readability when the rich text editor does not have enough space.

![9-25-2014 6-44-48 PM](/assets/img/2014/10/9-25-2014-6-44-48-pm.png)

¬[9-25-2014 6-45-29 PM](/assets/img/2014/10/9-25-2014-6-45-29-pm.png)

### Installation and Configuration

The following is the walkthrough video:

{% include embed/youtube.html id='ZFGPsTmsoBA' %}

#### What you need to know before you install

[This installation is not for production and can't be upgraded, the only purpose is for features evaluation and feedback]

![image023](/assets/img/2014/10/image023.jpg?w=541)

#### How to install and configure

Installation time: 20 minutes  
Configuration time: 5 minutes

This installation doesn't support the layout switch, so you will need to install the web installer.

![9-25-2014 4-34-11 PM](/assets/img/2014/10/9-25-2014-4-34-11-pm.png)

For the supported switches type `tfs_server.exe /?`

![9-25-2014 4-34-42 PM](/assets/img/2014/10/9-25-2014-4-34-42-pm.png)
