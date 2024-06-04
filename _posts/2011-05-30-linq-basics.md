---
layout: post
title:  "LINQ basics"
date:   2011-05-30 07:40:05 +0100
---

1.  Obtain the data sources(s)
2.  Create the query
    1.  Declare variable var query = the following
    2.  From variable Name in obtained data Source
        [//Declaration]
    3.  Where variable name. Property == or \> or \< or any operator
        against any value [// criteria and
        filtering]
    4.  Orderby variable name. Property, variable name. Property
        [//sorting]
    5.  Select (variable name or variable name \* 10 (any expression) or
        new { property1= val1 , property2 = val2 } (anonymous type) [//
        projection]
3.  Execute the query
    1.  ToList() 
    2.  ToArraay()
    3.  Foreach and access the query result

Example:

```csharp

var files = new DirectoryInfo(@"c:\\").GetFiles();

var query = from file in files
            where file.Length > 0
            orderby file.Name, file.Length
            select new 
            {
                Name = file.Name,
                Length = file.Length,
                CreatedDate = file.CreationTime
            };

var my = query.ToList();

foreach (var myFileInfo in query)
{
    Console.WriteLine(myFileInfo.Name);
}

```

