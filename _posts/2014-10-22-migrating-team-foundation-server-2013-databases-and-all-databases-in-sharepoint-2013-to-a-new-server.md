---
layout: post
title: "Migrating Team Foundation Server 2013 Databases and all Databases in SharePoint 2013 to a New Server"
date: 2014-10-22 20:17:22 +0100
---

This post could be used for many scenarios as the following:

**Scenario 1**: Migrate Team Foundation Server's SQL Server to another machine, Migrating Team Foundation Server Databases, moving TFS configuration Database to another SQL Server  
**Following steps**: Step-1, step-2, step-4, step-5, step-6, step-7, step-8, step-9, step-11, step-13

**Scenario 2**: Move all databases in SharePoint 2013, Moving SharePoint Content Databases to a New Server, Migrate SharePoint's SQL Server to another SQL Server, Moving SharePoint to a different SQL server  
**Following steps**: Step-1, step-3, step-4, step-5, step-7, step-10, step-12

**Scenario 3**: Migrating Team Foundation Server Databases and all databases in SharePoint 2013 to a New Server  
**Following steps**: All steps

The list of all steps:

1. Installing MS SQL Server 2014
2. Stop IIS and all TFS Services
3. Stop IIS and all SharePoint Services
4. Share a folder and turn off firewall
5. Backup DBs and store them on the shared folder
6. Backup SQL Server Reporting encryption key
7. Restore DBs to the new SQL Server machine
8. Remap Reporting DB and restore encryption key
9. Remap and configure TFS for the new DB server
10. Remap and configure SharePoint for the new DB server
11. Start IIS and all TFS Services again
12. Verify SharePoint DB migration
13. Verify TFS DB migration
14. Note-1 DotNet Framework cannot be installed
15. Note-2 Fix SharePoint error cannot open DB
16. Note-3 Fix SharePoint error cannot open sites
17. Note-4 Repair TFS connection with SharePoint
18. Note-5 Analysis DB backup and restore

### 1. Installing MS SQL Server 2014

{% include embed/youtube.html id='src418k9tUI' %}

### 2. Stop IIS and all TFS Services

{% include embed/youtube.html id='nDEIHZkRDdU' %}

### 3. Stop IIS and all SharePoint Services

{% include embed/youtube.html id='wRG6acZX4Js' %}


### 4. Share a folder and turn off firewall

{% include embed/youtube.html id='w5QShwlyLNM' %}

### 5. Backup DBs and store them on the shared folder

{% include embed/youtube.html id='p8xLn5Dy-gU' %}

### 6. Backup SQL Server Reporting encryption key

{% include embed/youtube.html id='KU6S-jGrbDg' %}

### 7. Restore DBs to the new SQL Server machine

{% include embed/youtube.html id='_cdH1XiBNrA' %}


### 8. Remap Reporting DB and restore encryption key

{% include embed/youtube.html id='YXOr7OoLNUU' %}

### 9. Remap and configure TFS for the new DB server

{% include embed/youtube.html id='Sij4Kmmhh6I' %}

### 10. Remap and configure SharePoint for the new DB server

{% include embed/youtube.html id='dtcdfilQar8' %}

### 11. Start IIS and all TFS Services again

{% include embed/youtube.html id='XUBUHL__gjo' %}

### 12. Verify SharePoint DB migration

{% include embed/youtube.html id='_DdipfiLZ0I' %}

### 13. Verify TFS DB migration

{% include embed/youtube.html id='BiLgM11gKfM' %}

### 14. Note-1 DotNet Framework cannot be installed

{% include embed/youtube.html id='aG8GeJRtu28' %}

### 15. Note-2 Fix SharePoint error cannot open DB

{% include embed/youtube.html id='aWaBYgv5KFU' %}

### 16. Note-3 Fix SharePoint error cannot open sites

{% include embed/youtube.html id='28j02EsLtS0' %}

### 17. Note-4 Repair TFS connection with SharePoint

{% include embed/youtube.html id='GHhs2-sE0fY' %}

### 18. Note-5 Analysis DB backup and restore
