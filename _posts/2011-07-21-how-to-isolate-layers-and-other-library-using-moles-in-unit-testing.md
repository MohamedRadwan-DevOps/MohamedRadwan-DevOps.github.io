---
layout: post
title: "How to isolate layers and other libraries using Moles in Unit Testing?"
date:   2011-07-21 21:44:51 +0100
---

Moles is one of the mocking frameworks for isolating dependencies and other layer\'s classes. I used to work with the Moq framework and it was very good, but with Moles you can do some things that I don\'t know if we can do with Moq. For example, you can isolate your code from .NET Framework code. How will you isolate `DateTime.Now` to return a specific value that you want? Remember that you don\'t have access to the definition of the .NET Framework classes, but with Moles, you can do that. 

I created a solution from multiple projects so we can investigate Moles. The solution structure is as follows:

![Solution Structure](/assets/img/2011/07/7-21-2011-5-13-39-PM.png)

![Project Structure](/assets/img/2011/07/7-21-2011-5-13-58-PM.png)

You will add a reference in the Test project to the DB project. Right-click on the DB reference and choose Add Mole Assembly.
![Add Mole Assembly](/assets/img/2011/07/7-21-2011-5-16-27-PM.png)

![Mole Assembly](/assets/img/2011/07/7-21-2011-6-05-42-PM.png)

Start using it as follows:

**DB Class**
```csharp
using Common;

namespace DB 
{ 
    public class DataBase : IDataBase 
    { 
        public bool Save(IEmployee e) 
        { 
            return true; 
        } 
    } 
}
```
**Employee Class**

```csharp
using System;
using Common;

namespace DB 
{ 
    public class Employee : IEmployee 
    { 
        public int Id { get; set; } 
        public string Name { get; set; } 
        public DateTime BirthDate { get; set; } 
    } 
}
```

**The method under Test**

```csharp
using System;
using Common;
using DB;

namespace TryMole 
{ 
    public class MyClass 
    { 
        public IDataBase DataBase { get; set; }

        public void SaveEmployee(IEmployee e) 
        { 
            if (e == null) throw new ArgumentNullException();
            if (e.Id <= 0) throw new ArgumentException();
            if (e.Id > 5000) throw new ArgumentException();
            
            DataBase.Save(e);
        } 
    } 
}

```
**Test Method**

```csharp
[TestMethod()]
public void SaveEmployeeTest() 
{
    MyClass target = new MyClass(); // TODO: Initialize to an appropriate value
    var database = new SIDataBase();
    database.SaveIEmployee = (IEmployee emp) => true;
    target.DataBase = database;

    IEmployee e = new Employee { Id = 5 };
    target.SaveEmployee(e);
}

```


I included also a project that isolate .NET Framework DateTime to return 1/1/2000 Y2K Bug To download
the project and Y2K project click the following link
[download](https://skydrive.live.com/#!/?cid=4bcaa16d27b46600&sc=documents&uc=2&id=4BCAA16D27B46600%211898 "Download")

