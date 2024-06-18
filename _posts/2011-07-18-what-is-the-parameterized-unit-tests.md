---
layout: post
title: "What is the parameterized unit tests?"
date:   2011-07-18 10:59:21 +0100
---

Before answer this question we have to answer the question what is
classic unit test?

-   Classic unit test

Classic or closed unit test is the normal unit test
that doesn\'t take parameter and depend on static data inside the method
itself, using traditional unit tests that do not take inputs lead that
you have to write many tests to cover all possible inputs 

```csharp
[TestMethod]
public void MyTestMethod() 
{
    int x = 5;
    int y = 10;
}

```

-   Parameterized unit test

Parameterized unit tests are test methods with parameters. A
straightforward extension is to allow parameters, which serve as the
test input. The result is a parameterized unit test 

```csharp
[TestMethod]
public void MyTestMethod(int x, int y) 
{ 

}
```

So classic unit tests are methods without
parameters, parameterized unit tests are methods with parameters. So you
can use it with Data driven test from DB or Excel sheet, or you can use
it with many inputs as needed You can partition parameterized unit tests
into four parts:

1.   Assume: Assume preconditions over the test inputs.
2.   Arrange: Set up the unit under test-determine which parameters are
    used to shape legal test inputs.
3.  Act: Exercise the unit under test by adding a method sequence, which
    specifies a scenario, and capturing any resulting state. You use
    parameters for argument values when calling other methods in the Act
    stage.
4.  Assert: Verify the behavior by adding assertions that encode the
    rules of a unit test.

```csharp
[PexMethod]
public void ContainsNumbers(string number, Employee employee, [PexAssumeNotNull] string value) 
{ 
    PexAssume.IsTrue(employee != null);
    PexAssert.TrueForAll(number, delegate(char c) 
    { 
        return char.IsDigit(c);
    }); 
}
```



