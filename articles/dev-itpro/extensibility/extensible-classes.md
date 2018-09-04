---
# required metadata

title: Writing extensible classes
description: This article how to write extensible methods.
author: Smitha Nataraj, Lars-Bo
manager: AnnBe
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: Smitha Nataraj, Lars-Bo
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Classes

[!include [banner](../includes/banner.md)]

A class and its methods should have a single responsibility, which makes it a lot easier to extend going forward.

In essence, it is all about writing small cohesive methods with good names.  Each public and protected method is an extensibility point, so each time a new method is introduced it is enabling downstream consumers to inject additional logic to the method.  

A simple example:

**Not extensible code:**

```
    void calculatePrice(SalesLine _saleLine, AmountMST _amount)
    {
        // cannot add extra condition if needed
        if(_saleLine.QtyOrdered > 0 && _saleLine.SalesType == SalesType::Sales)
        {
            ttsbegin;
            // calculation of SalesPrice is locked and cannot be extended
            _saleLine.SalesPrice = _saleLine.QtyOrdered * _amount;
            _saleLine.update();
            ttscommit;
        }
    }
```

**Extensible code:**

```
 protected boolean canUpdateSalesPrice(SalesLine _saleLine)
    {
        return (_saleLine.QtyOrdered > 0 &&
    _saleLine.SalesType == SalesType::Sales);
    }
 
    protected SalesPrice calculateSalesPrice(
    SalesLine _saleLine, AmountMST _amount)
    {
        return _saleLine.QtyOrdered * _amount;
    }
 
    public void updateSalesPrice(SalesLine _saleLine, AmountMST _amount)
    {
        // extra condition can be added in CoC on the method
        if(this.canUpdateSalesPrice(_saleLine))
        {
            ttsbegin;
            // extra calculation/value can be added in CoC on the method
            _saleLine.SalesPrice = this.calculateSalesPrice(_saleLine, _amount);
            _saleLine.update();
            ttscommit;
        }
    }
```

## Class hierarchies

For **new class hierarchies** or for existing class hierarchies where a factory pattern can be used, using the ```SysExtension``` framework enables easy extensions:
+ **Truly decoupled** - New subclasses can be added without any changes to the base class. 
+ **Less code** is required.
+ **No change in the public API** - the contract of the construct stays the same; hence, this is an easy and low risk refactoring. 
	
For **existing factory methods** which are not instantiating sub-classes using the instance constructor (and instead calls a static constructor like ```construct```), using the ```SysExtension``` framework would lead to a breaking change, as the static constructors on the sub-classes are no longer invoked. Use the ```SysExtension``` framework only for the default case, in such cases.
	
Read more:
+ [https://blogs.msdn.microsoft.com/mfp/2013/06/12/sysextension-framework-to-the-rescue/](https://blogs.msdn.microsoft.com/mfp/2013/06/12/sysextension-framework-to-the-rescue/)
+ [https://blogs.msdn.microsoft.com/axinthefield/embrace-the-extensions-mindset-with-dynamics-365-for-finance-and-operations-2-sysextension-framework/ ](https://blogs.msdn.microsoft.com/axinthefield/embrace-the-extensions-mindset-with-dynamics-365-for-finance-and-operations-2-sysextension-framework/)


## Deprecation

If a class or a public/protected method is no longer needed - Always obsolete the method with a warning first, and at a point in future when all consumers have had the chance to uptake the changes and/or new API, the method can then be deprecated. Deprecating classes, methods or removing class members is otherwise a breaking change. See more in [breaking changes](BreakingChanges.md). 

