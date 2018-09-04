---
# required metadata

title: Write extensible classes
description: This article provides information about how to write extensible methods.
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

# Write extensible classes

[!include [banner](../includes/banner.md)]

A class and its methods should have a single responsibility. By writing small cohesive methods wtih good names, it is easier to extend going forward. Each public and protected method is an extensibility point. Each time a new method is introduced, it is enabling downstream consumers to inject additional logic to the method.  

### Example

**Not extensible code**

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

**Extensible code**

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
For new or existing class hierarchies where a factory pattern can be used, using the ```SysExtension``` framework enables easy extensions. These extensions are truly decoupled allowing new subclasses to be added without any changes to the base class. Less code is required and because the contract of the construct remains the same, there is no change to the public API which results in low risk refactoring.
	
For **existing factory methods** which are not instantiating sub-classes using the instance constructor, and instead calling a static constructor like ```construct```, using the ```SysExtension``` framework would lead to a breaking change. This is because the static constructors on the sub-classes are no longer invoked. In these situations, use the ```SysExtension``` framework only for the default case.
	
For more information about class hierarchies, see the following blog posts:
+ [SysExtension Framework – to the rescue](https://blogs.msdn.microsoft.com/mfp/2013/06/12/sysextension-framework-to-the-rescue/)
+ [Embrace the extensions mindset with Dynamics 365 for Finance and Operations #2 – SysExtension framework](https://blogs.msdn.microsoft.com/axinthefield/embrace-the-extensions-mindset-with-dynamics-365-for-finance-and-operations-2-sysextension-framework/)

## Deprecation
If a class or a public or protected method is no longer needed, always obsolete the method with a warning first, and then, when all consumers have had the chance to uptake the changes or new API, the method can be deprecated. Deprecating classes and methods, or removing class members otherwise, is a breaking change. For more information, see [Breaking changes](BreakingChanges.md). 

