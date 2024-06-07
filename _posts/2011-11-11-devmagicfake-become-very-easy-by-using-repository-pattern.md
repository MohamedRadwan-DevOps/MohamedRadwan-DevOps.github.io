---
layout: post
title: "DevMagicFake become very easy by using Repository Pattern"
date:   2011-11-11 06:41:40 +0100
---

One of the best pattern I used is **Repository Pattern**, for more
information see this

[link](http://martinfowler.com/eaaCatalog/repository.html "RepositoryPattern"), it helps me to apply the PI of the DDD and it fit in Layered architecture of DDD, I made a big research against using Generic Repository as my previous project or vs.Specific Repository?  as I saw too much in the community, and after details research I decide to use
combine of both for many reasons,  this will help me reuse the code but with  more control than just only Generic Repository, any way I will not dig more about **Repository Pattern** I just need to clue my idea so you
can get my point of the next explanation I will provide about

[DevMagicFake](https://mohamedradwan.com/category/dev-magic-fake/ "DevMagicFake") 

Now DevMagicFake implement the **Repository Pattern **and this will help us very well in to reduce the thrown or maintenance code with DevMagicFake as we do before, because in real development we really call
the method that we need from our real repository By using IRepository interface which will be implemented by DevMagicFake and real repository, so no need to throw all faking code that used by DevMagicFake, unless
some code like generating object with data that of course will not existing in IRepository interface Here is the IRepository interface

```csharp
using System;
using System.Collections.Generic;
using System.Linq.Expressions;

public interface IRepository<T> where T : class
{
    T Add(T entity);
    T Get(Expression<Func<T, bool>> where);
    IEnumerable<T> GetAll();
    T GetByCode(string code);
    T GetById(long id);
    IEnumerable<T> GetMany(Expression<Func<T, bool>> where);
    void Remove(T entity);
    void Remove(Expression<Func<T, bool>> where);
}
```

Here is how we will use it in our controller. As we can see, the controller will
take a parameter of type IVendorRepository, which is a specific repository
that implements the IRepository interface.

```csharp
public class VendorController : Controller
{
    private IVendorRepository vendorRepository;

    public VendorController(IVendorRepository vendorRepository)
    {
        this.vendorRepository = vendorRepository;
    }

    public ActionResult List(VendorListModel vendorListModel)
    {
        var vendors = this.vendorRepository.GetAll();
        var vendors2 = this.vendorRepository.GetMany(v => v.Code > 50).ToList();

        // REMOVEFAKE: FakeNote
        // Begin Faking
        var generatedVendors = ((FakeRepository<Vendor>)vendorRepository).Create(10);
        // End Faking

        return View(vendors);
    }
}
```


[Note: this feature not released yet, so if anyone
need to use it, he will need to download the latest reversion of
the project from CodePlex and just make a local build on his
machine.]

Remember, we will use any IoC or Dependency Injection to inject DevMagicFake or real repository or Mocking at the run time, this depend on the working stage, if its Faking, Testing, Development or Real stage So now we are not only reduce the faking code that produced by DevMagicFake but we also transform this faking code into real development code which will enhance our productivity , we also control the faking code by using the 
[fakingsnippet](https://mohamedradwan.com/2011/11/10/1031/ "FakeSnippet")  
so we can track and trace any faking or debts code at anytime! 

Thanks

