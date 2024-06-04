---
layout: post
title: "Adapter Pattern"
date:   2010-10-20 07:40:05 +0100
---

## Summary

Adapter pattern converts the interface of a class into another interface clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces. It is also known as a Wrapper.

## Example and Reasons

In the .NET library, we cannot change the library interface since we may not have its source code. Even if we did have the source code, we probably should not change the library for each domain-specific application.

## Solution

We will create our adapter for our domain that adapts the interface to match our needed interface.

## Participants
- Target
- Adapter
- Adaptee
- Client
- Factory

## Class Adapters
- Simple and invisible to the client.
- A class adapter has an instance of an interface and inherits a class.
- Overriding behavior can be done more easily with a class adapter.

## Use the Adapter Pattern When You Want To:
- Create a reusable class to cooperate with yet-to-be-built classes.
- Change the names of methods as called and as implemented.
- Use an existing class, and its interface does not match the one you need.

[![image001](/assets/images/2010/05/image001.jpg)](/assets/images/2010/05/image001.jpg)

## Classes

```csharp
public class Client1
{
    public void AnyMethod()
    {
        // Target t = Factory.CreateTarget();
        Target t = new Target();
        // Client1 uses the target interface "Request"
        t.Request();
    }
}

public class Target
{
    public virtual void Request()
    {
        Console.WriteLine("Called Target Request()");
    }
}

public class Adapter : Target
{
    private Adaptee _adaptee = new Adaptee();
    public override void Request()
    {
        // Possibly do some other work
        // and then call SpecificRequest
        _adaptee.SpecificRequest();
    }
}

public class Adaptee
{
    public void SpecificRequest()
    {
        Console.WriteLine("Called SpecificRequest()");
    }
}

public class Factory
{
    public static Target CreateTarget()
    {
        return new Adapter();
        // or
        // return new Target();
    }
}

```

You can see the following video for more information.

{% include embed/youtube.html id='fXeBw7yFGnE' %}
