---
layout: post
title: "Generate unit tests and run them with CI (Continuous integration) using Pex and MS Team Build 2010"
date:   2011-07-19 13:29:27 +0100
---

#### Continuous Integration + Microsoft Pex = Continuous Exploration

By exploring our code with Microsoft Pex in our continuous integration, we will leverage the full power of automated test generation.

- First let's define what is Pex in a nutshell?

Pex is a white box testing framework that does the following:

1. Generate parameterized unit tests if they do not exist
2. Run Pex Exploration on parameterized unit tests
3. Generate unit tests with inputs depending on two things:
   1. The code of the method under test
   2. The precondition of the test data and parameters in the parameterized unit test (PexAssume)
4. Identify if the generated unit tests will succeed or fail when they run

So I can integrate Pex into CI (Continuous Integration) as follows:

**Preconditions:**

Pex will be used for the Domain and the DAL layer. I will not use Pex in the Controller or the Presentation layer (MVC).

**First scenario:**

1. The developer uses Pex in his/her day-to-day development tasks since he/she is working on the Domain or the DAL layer.
2. The developer starts creating the parameterized unit test manually and adds any precondition as needed (PexAssume, ExpectException, etc.).
3. The developer runs Pex Exploration on his/her manual parameterized unit test and sees if there is any generated method that will fail. If so, he/she adjusts the parameterized unit test by adding PexAssume, ExpectException, and so on until all generated test methods become green, indicating that they will pass if they run.
4. The developer checks in his code (code under test and the manual parameterized unit test) into the source control.
5. The build starts and runs Pex Exploration against the manual parameterized unit test, generates the unit tests, and checks if any unit test fails, causing the build to fail.

```xml
pex.exe MyApplication.Tests.dll /nor /ftf
```

**Second scenario:**

1.  The developer didn\'t use Pex at all, the developer may use Pex for
    personal check only before check-in his code, the parameterize unit
    test will not checked-in ++in the source++control
2.  The developer start develop on the application
3.  The developer check-in his code in the source++control
4.  The build start and run Pex to generate++++parameterize unit test
5.  The build++run Pex Explortion against the generated parameterize unit
    test and generate the unite tests and see if they has any unit test
    that fail so the build will fail


```xml
pex.exe MyApplication.dll /nor /ftf /erm:wizard

```


