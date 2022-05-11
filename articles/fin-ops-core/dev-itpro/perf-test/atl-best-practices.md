---
title: Best practices for the Acceptance test library
description: This topic provides best practices for the Acceptance test library.
author: MichaelFruergaardPontoppidan
ms.date: 03/27/2019
ms.topic: article
ms.prod: 
ms.technology: 

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2019-03-27
ms.dyn365.ops.version: App Update 10.0.2

---

# Best practices for the Acceptance test library

[!include [banner](../includes/banner.md)]

## Use var and declare variables inline

+ Use the `var` keyword (type inference).
+ Declare variables inline instead of in a separate statement.

### Do this

```xpp
var item = items.default(); 
var salesOrder = data.sales().salesOrders().createDefault();
var salesLine = salesOrder.addLine().setItem(item).setInventDims([warehouse]).setQuantity(10).save();
```

### Don't do this

```xpp
InventTable item; 
AtlEntitySalesOrder salesOrder;
AtlEntitySaleOrderLine salesLine;
…
item = items.default(); 
salesOrder = data.sales().salesOrders().createDefault();
salesLine = salesOrder.addLine().setItem(item).setInventDims([warehouse]).setQuantity(10).save();
```

### Justification

The advantages of using `var` are that you write less code, you don't have to remember exact type names, and the test logic isn't cluttered with unimportant information. Overall, the test code easier to read.

In the previous example, it doesn't matter whether `item` is of the `ItemId`, `InventlTable`, or `AtlEntityInventItem` type. The important detail is that you're creating a sales line that has a well-known default item. The exact types of the `salesOrder` and `salesLine` variables aren't important. The contracts of these types are clear from the naming and usage.

### Considerations

- Don't use type inference if you want compilation to fail if the return type of a method changes.
- Don't use type inference if you can't invent meaningful variable or method names.

## Use entities instead of IDs as method parameters

Well-known data methods, creator methods, and `init` methods usually return records or entities instead of IDs. We recommend that you use records or entities as method parameters.

### Do this

```xpp
var salesLine = salesOrder.addLine().setItem(item).save();
```

### Don't do this

```xpp
var salesLine = salesOrder.addLine().setItemId(item.ItemId).save();
```

### Justification

The code is easier to read, because it isn't cluttered with unimportant technicalities.

### Considerations

If you know only the ID, use the method that takes the ID as an argument.

## Use navigation node shortcuts

When you automate a new domain area, introduce a base class that holds shortcuts to the most frequently used navigation objects in that area.

For example, for the warehouse management area, there is a base class that is named `AtlWHSTestCase`. It contains shortcuts to `data.whs()`, `data.invent()`, `data.invent().items()`, `data.invent().units()`, and other navigation objects. The shortcuts simplify your test code.

```xpp
class AtlWHSTestCase extends SysTestCase
{
    AtlDataRootNote          data;
    AtlDataInvent            invent;
    AtlDataInventOnHand      onHand;
    AtlDataProductItems      items;
    AtlDataWHS               whs;

    protected void initDataSetupReferences()
    {
        data = new AtlDataRootNode();
        invent = data.invent();
        onHand = data.invent().onHand();
        items = data.invent().items();
        whs = data.whs();
```

It also makes sense to introduce shortcuts that are shared among many test methods in the same class.

### Do this

```xpp
class WHSMinMaxReplenishmentScenarioTest extends AtlWHSTestCase
…
    var item = items.default(); 
    var warehouse = invent.warehouses().default(); 
```

### Don't do this

```xpp
class WHSMinMaxReplenishmentScenarioTest extends SysTestCase
…
    var item = data.invent().items().default(); 
    var warehouse = data.invent().warehouses().default(); 
```

### Considerations

You don't have to create a shortcut for every navigation node that you need. However, consider creating them for the navigation nodes that are frequently used.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]