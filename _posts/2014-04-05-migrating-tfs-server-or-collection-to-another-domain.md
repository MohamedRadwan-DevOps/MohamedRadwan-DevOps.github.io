---
layout: post
title: "Migrating TFS Server or Collection to another domain"
date:   2014-04-05 23:50:46 +0100
---

If you migrating a TFS Server or a Collection to another domain? You
will need to be very careful about Service and User Accounts, you will
need a well plan for that, otherwise it will end up with a big mess.

**Scenario 1, the same accounts with different domain name:**

```xml
Identities /change /fromdomain:Domain1 /todomain:Domain2 
```

**Scenario 2, different accounts with different domainname:**

-   You will need to manually map one by one as the following:

```xml
TFSConfig Identities /change
/fromdomain:Domain1 /todomain:Domain2 /account:OldAccount
/toaccount:NewAccount 
```

- And the following is the command for mapping the service account for AT (Application Tire)

```xml
TFSConfig
Accounts /change /AccountType:ApplicationTier /account:AccountName
/password:Password 
```

**So what are the steps to map myb accounts:** 

-   Create all the new accounts on the new domain and[ DON\'T ADD THEM
    TO TFS]
-   Open the command line as admin and navigate to \"*C:Program
    FilesMicrosoft Team Foundation Server 12.0Tools*\"
-   Run the TFSConfig Identities with the right parameters
-   Review the result
-   Force synchronization for fasting the retrieving the result or wait
    the synchronization to happen after sometimes

**Create all the new accounts on the new domain and[ DON\'T ADD THEM TO
TFS 

![Add user accounts to the domain](/assets/img/2014/03/add-user-accounts-to-the-domain.png)

**Open the command line as admin and navigate to** 

\"*C:Program FilesMicrosoft Team Foundation Server 12.0Tools*\" 

![Navigate to TFS Tools](/assets/img/2014/03/navigate-to-tfs-tools.png)

**Run the TFSConfig Identities with the right parameters**

![Run TFSConfig with parmeters](/assets/img/2014/03/run-tfsconfig-with-parmeters.png)

**Review the result** 

![map to a user exist on the domain but not added to TFS](/assets/img/2014/03/map-to-a-user-exist-on-the-domain-but-not-added-to-tfs.png)


**Force synchronization for fasting the retrieving the result or wait the synchronization to happen after sometimes** see the following post on how to do that: [Force Synchronizing TFS 2013 Users with Windows Accounts](https://mohamedradwan-devops.github.io/posts/force-synchronizing-tfs-2013-users-with-windows-accounts/ "Force Synchronizing TFS 2013 Users with Windows Accounts")

**What will happen if I mapped to an exiting user on the TFS?**

![map to user exist on the domain and added to TFS](/assets/img/2014/03/map-to-user-exist-on-the-domain-and-added-to-tfs.png)

**What will happen if I mapped to account that is not existing?**

![Map to user that is not exist on the domain](/assets/img/2014/03/map-to-user-that-is-not-exist-on-the-domain.png)

For more info see the following link: [Move Team Foundation Server from one environment to another](http://msdn.microsoft.com/en-us/library/ms404883.aspx#MoveAccounts "Move Team Foundation Server from one environment to another")

[TFS Integration Tools - How do I map users between domains or systems? ](http://blogs.msdn.com/b/willy-peter_schaub/archive/2011/02/05/tfs-integration-tools-how-do-i-map-users-between-domains-or-systems-q-amp-a-44.aspx?Redirected=true "TFS Integration Tools - How do I map users between domains or systems? ")

