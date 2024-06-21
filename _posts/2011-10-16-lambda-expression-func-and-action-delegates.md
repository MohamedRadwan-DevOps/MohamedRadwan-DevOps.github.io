---
layout: post
title: "Lambda Expression, Func and Action delegates"
date:   2011-10-16 05:35:57 +0100
---

Finally I decide to post this topic, every time I said it\'s not
needed because it\'s very simple topic, but I always take time to
remember all it\'s details specially when i get busy with TFS workflow,
build automation, deployment automation and all other process automation
stuff, when I get back to C# code I take time to remember these small
things, so I decide to post it to be remembered quickly

-   **Func**\<\>

I will start by talking about [Func]\<\> so
what is it? Built-in delegates that take none or one or many parameters
and return one result, as we can see we have 16 overloading start from
the first one that didn\'t take any parameters and return one result and
ending with the final one that take 15 parameters and return one result
too

[![](/assets/img/2011/10/Func-delegates.png)](/assets/img/2011/10/Func-delegates.png)

Remember that always the last parameter is the return parameter Why
these delegates exist? because .NET Framework use them in LINQ and
Extension method so Microsoft makes them public so that we as developers
can use them instead of creating new delegates with the same signature

- **Action**\<\>

The same as Func but it doesn\'t return value (void)

[![](/assets/img/2011/10/Action-delegates.jpg)](/assets/img/2011/10/Action-delegates.jpg)

-  **Lambda Expression**

So let\'s see the following example: 

```csharp
public static int MyMethod(Func<int, int> del)
{
    return del(4);
}

```

So we can see that this method takes a parameter as
delegate, that\'s mean we will pass a method as a parameter with the
same signature of the delegate So we can make method that take one
[int] and return [int]
as the signature of the [Func](parameter) as
the following method 

```csharp
public static int MethodParameter(int x)
{
    return x += 5;
}

```

And then we will path it to our method (MyMethod) 

```csharp
MyMethod(MethodParameter)
```
But why we create method that we will not use it anymore??? And here the
anonymous method will take place, so instead of creating method and pass
it to MyMethod we will pass anonymous method with the same signature So
how to write anonymous method with the same signature? it\'s very
simple, we just write the method and remove the first part until the
parameter and write delegate instead of the first part as the following:

[![](/assets/img/2011/10/Anonymous-Method.png)](/assets/img/2011/10/Anonymous-Method.png)

So it will become as the following: 

```csharp
Func<int, int> myDelegate = delegate(int x) 
{
    return x += 5;
};

```

So now we can pass the anonymous method to MyMethod as the
following:

```csharp
MyMethod(delegate(int x)
{
    return x += 5;
});

```

So now we will convert the anonymous method to lambda expression and pass it to
MyMethod but first how we can convert anonymous method to lambda
expression? It\'s very simple

```csharp
// anonymous method
MyMethod(delegate(int x) 
{
    return x += 5;
});

// lambda expression with explicit parameter type
MyMethod((int x) => 
{
    return x += 5;
});

// lambda expression with inferred parameter type
MyMethod(x => 
{
    return x += 5;
});

// simplified lambda expression (single statement, no curly braces needed)
MyMethod(x => x += 5);

```

So now instead of pass anonymous method to MyMethod we
will pass the lambda expression of the anonymous method as the
following:

```csharp
MyMethod(x => x += 5);

```

We don\'t need to express the logic of our delegate in
the lambda expression. We can as easily call a method, like
this:

```csharp
prod => EvaluateProduct(prod)

```

If we need a lambda expression for a delegate that has
multiple parameters, we must wrap the parameters in parentheses, like
this:

```csharp
(prod, count) => prod.Price > 20 && count > 0

```

And finally, if we need logic in the lambda
expression that requires more than one statement, we can do so by using
braces ({}) and finishing with a return statement, like
this:

```csharp
(prod, count) => 
{
    // ...multiple code statements
    var result = prod.Price > 20 && count > 0;
    return result;
    // Notice here because multiple parameters we have Parentheses
    // And also because we have many statements we have curly brackets
}
```
I hope it helps

