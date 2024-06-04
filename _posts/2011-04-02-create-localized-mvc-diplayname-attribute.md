---
layout: post
title:  "Create a localized version of DisplayName attribute for MVC"
date:   2011-04-02 07:40:05 +0100
---

As most of my followers know I am now working on MVC Enterprise project and when the time come to start refactoring my team code I found that, they didn\'t use DsipalyName attribute to read from the resource file (No hard coded string to support multilingual) and when I search why they doing this I found that there is no one, so I decide to create an extension method that support this feature, of curse I search on the internet and I found a solution included in a new feature in MVC (MVC Futures release. 

[see this article](http://weblogs.asp.net/rajbk/archive/2010/04/27/localization-in-asp-net-mvc-2-using-modelmetadata.aspx "MVC features release"))

but it needs some configuration and I don\'t want any new modification to my project until I completely convert it to MVC 3.0 RTM soon. so here my custom method to create a localized version of  DsipalyName
attribute. So first I will create a class that override DisplayName

```csharp
using System;
using System.ComponentModel;
using System.Reflection;
using System.Resources;

namespace Radwan 
{
    public class DisplayNameLocalizedAttribute : DisplayNameAttribute 
    {
        private readonly string resourceFileName;
        private readonly string resourceKey;
        private readonly Type type;

        public DisplayNameLocalizedAttribute(Type type, string resourceKey) 
        {
            this.type = type;
            this.resourceKey = resourceKey;
        }

        public override string DisplayName 
        {
            get 
            {
                return new ResourceManager(this.type.FullName, Assembly.GetExecutingAssembly()).GetString(this.resourceKey);
            }
        }
    }
}

```
so now I can call the new version like the following:

```csharp
public class Employee : IEmployee 
{
    public int Id { get; set; }

    [DisplayNameLocalized(typeof(ResourceFileName), "Name")]
    public string Name { get; set; }
}

```

That\'s it.

