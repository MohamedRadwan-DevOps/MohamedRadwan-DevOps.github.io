---
layout: post
title:  "Yield return, what does it mean?"
date:   2011-02-02 07:40:05 +0100
---

Yield return, it\'s a very strong keyword, all the LINQ to object use it when we use **foreach** or yield return. It is used to iterate through acollection returned by a method. you can create methods that return a ollection and don\'t have to go through declare and maintain it\'s state the compiler will do it for you, what does it means? To understand the different lets see code that doesn\'t use yield and code does
Without yield 

```csharp
class Program 
{
    static void Main(string[] args) 
    {
        foreach (int i in GetInt()) 
        {
            Console.WriteLine(i.ToString());
            Console.Read();
        }
    }

    public static IEnumerable<int> GetInt() 
    {
        List<int> nums = new List<int>();
        for (int i = 0; i < 5; i++) 
        {
            nums.Add(i);
        }
        return nums;
    }
}

```

With yield 

```csharp
class Program 
{
    static void Main(string[] args) 
    {
        foreach (int i in GetInt()) 
        {
            Console.WriteLine(i.ToString());
            Console.Read();
        }
    }

    public static IEnumerable<int> GetInt() 
    {
        for (int i = 0; i < 5; i++) 
        {
            yield return i;
        }
        yield return 20;
        yield return 30;
    }
} 
```
You can see here the different that you don\'t need to declare a variable to hold the return collection from your method you just need to yield return the variable and if you make a break point and execute each method you will notice how this method has different execution path, because without yield the **foreach** of the **GetInt** has to be finished first and then populate the collection variable but in other case it will return after each iteration, so it will return what you real need as you need it, so it will continue in the second method where it stop. In other word it will get iterate to bring the first number and then the caller will return to the first method \"**Main**\" and then when the method inside the **Main** call the second method it will go to iterate and bring the second number and return and so on.

