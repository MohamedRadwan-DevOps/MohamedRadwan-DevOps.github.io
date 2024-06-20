---
layout: post
title: "Re-throwing Exception, Custom Exception"
date: 2013-05-28 18:11:00 +0100
---

This is a very straightforward post where I want to highlight some important notes about exception **Re-throwing**.

### **Why Re-throw Exceptions?**

We re-throw exceptions in many cases, for example:

- **For logging**: We catch and re-throw the original exception to keep a log of what happened.
- **For security purposes**: We don't want to reveal sensitive information to all users, as it may be used to hack the system. Instead, we log the original exception and re-throw a general exception, such as "The process can't be done at this time," so that admin users can go to the event log or logging location for detailed information.
- **For using business exceptions**: Sometimes, we want to use custom exceptions to reflect alternative scenarios in our business workflow, for example:
  - `InvalidPasswordException`
  - `InsufficientFundException`
  - Etc.

When we re-throw an exception for logging, we use `throw` without an object because using `throw ex` changes the stack trace to indicate that the exception originated from the current location, which is not accurate.

```csharp
try 
{
    // code that may throw an exception
} 
catch (Exception) 
{
    throw; // re-throwing the original exception
}
```

When we create our custom exception, it\'s better to make it **Serializable** and to do that fast it\'s better to use Exception snippet

```csharp
using System.Runtime.Serialization;

[Serializable]
public class MyException : Exception 
{
    public MyException() { }
    public MyException(string message) : base(message) { }
    public MyException(string message, Exception inner) : base(message, inner) { }
    protected MyException(SerializationInfo info, StreamingContext context) : base(info, context) { }
}

```

