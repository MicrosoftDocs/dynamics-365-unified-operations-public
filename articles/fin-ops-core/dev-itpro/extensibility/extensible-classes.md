---
title: Write extensible classes
description: Learn about how to write extensible classes, including examples of non-extensible code and extensible code with overviews of class hierarchies and deprecation.
author: smithanataraj
ms.author: smnatara
ms.topic: article
ms.date: 09/09/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible classes

[!include [banner](../includes/banner.md)]

A class and its methods should have a single responsibility. Keep the following in mind in order to design classes that are resilient to changes in the long run. Class should have:

+ A clear purpose
+ Good names (class name and method names)
+ Only methods that should be extended are exposed for extensibility, i.e. the key rule is allow extending as little as necessary.
	- Every public and protected method is an extensibility point in X++. Every time that a new method is introduced, downstream consumers get a new way to inject additional logic into the method.

### Example

**Non-extensible code**

```xpp
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

```xpp
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
For new or existing class hierarchies where a factory pattern can be used, the SysExtension framework enables easy extensions. Because these extensions are truly decoupled, new subclasses can be added without requiring any changes to the base class. Therefore, less code is required. Additionally, because the contract of the construct remains the same, there is no change to the public application programming interface (API). Therefore, refactoring involves low risk.
	
Some existing factory methods might not instantiate subclasses by using the instance constructor. Instead, they might call a static constructor, such as **construct**. If the SysExtension framework is used for these factory methods, a breaking change occurs, because the static constructors on the subclasses are no longer invoked. In these situations, use the SysExtension framework only for the default case.
	
For more information about class hierarchies, see the following blog posts:

+ [SysExtension Framework – to the rescue](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/sysextension-framework-to-the-rescue)
+ [Embrace the extensions mindset with Dynamics 365 for Finance and Operations #2 – SysExtension framework](https://community.dynamics.com/ax/b/axinthefield/posts/embrace-the-extensions-mindset-with-dynamics-365-for-finance-and-operations-2-sysextension-framework)

## Deprecation
If a class or a public or protected method is no longer required, always use a warning first to notify consumers that the method is obsolete. Then, when all consumers have had the chance to uptake the changes or the new API, the method can be deprecated. Deprecation of classes and methods (or removal of class members in other cases) is a breaking change. For more information, see [Breaking changes](breaking-changes.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
