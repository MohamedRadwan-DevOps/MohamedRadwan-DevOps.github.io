---
layout: post
title: "Extension Methods for IEnumerable of T and Custom Collection"
date:   2011-10-17 00:46:56 +0100
---

Custom Collection is one of the best design patterns I have ever used. It encapsulates items or an array of items inside a separate class, allowing us to fully control these items. However, for modern development, it is rare to see custom collections in any post or code snippet. When I deeply searched for why the community doesn't follow this pattern, I found that the community not only avoids this pattern but also recommends against it. The Microsoft .NET Framework Design Guide advises against it:
[http://msdn.microsoft.com/en-us/library/ms229042.aspx](http://msdn.microsoft.com/en-us/library/ms229042.aspx "MS Design Guidance")
[http://stackoverflow.com/questions/1544800/custom-collection-vs-generic-collection-for-public-methods](http://stackoverflow.com/questions/1544800/custom-collection-vs-generic-collection-for-public-methods "Stack Overflow ")

So, what is the main reason for this? The answer is **Extension Method**. Microsoft extends all the old collections like arrays, `List<T>`, `Queue<T>`, `Stack<T>`, `Dictionary<T, T>`, etc., with all extension methods in `System.LINQ`. So, there is no need to create custom collections. We just need to use `IEnumerable<T>` or `IList<T>` and then extend them at any time in our project with new extension methods. However, be careful, as this will not break the access of the members. In other words, the extension method will not be able to access private members like a custom collection does, but in most cases, this will be good enough.

- Extension Method for `IEnumerable<T>`

We can create extension methods that apply to an interface, allowing us to call this method for each class that implements this interface. For example, if we add an extension method called `CalculateSalary` for `IEnumerable<Employee>` as follows:

```csharp
public static decimal CalculateSalary(this IEnumerable<Employee> empList)
{
    decimal totalSalary = 0m;
    foreach (var employee in empList)
    {
        totalSalary += employee.Salary;
    }
    return totalSalary;
}
```

Now, I can create a list of `Employee` and I will find the method exists in this list as follows:

```csharp
static void Main(string[] args)
{
    IEnumerable<Employee> employees = new List<Employee>
    {
        new Employee { Id = 1, Salary = 49m },
        new Employee { Id = 2, Salary = 33m },
        new Employee { Id = 4, Salary = 66m }
    };
    Console.WriteLine(employees.CalculateSalary());
    Console.ReadLine();
}

```

**Extension Method Rules**

- It must be static and exist in any static class.
- It will extend the first parameter, which is prefixed with this.
- It will pass the current instance of the extended class at runtime.
- If you extend an interface, it means you extend any class that implements that interface.


