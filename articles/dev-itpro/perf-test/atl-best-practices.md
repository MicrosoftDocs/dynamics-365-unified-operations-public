---
# required metadata

title: Acceptance test library best practices
description: This topic provides information about the acceptance test library.
author: MichaelFruergaardPontoppidan
manager: AnnBe
ms.date: 03/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: MichaelFruergaardPontoppidan
ms.search.validFrom: 2018-XX-XX
ms.dyn365.ops.version: App Update 10.0.2

---

# Acceptance test library best practices

## Use `var` and declare variables inline

+ Use the `var` keyword (type inference). 
+ Declare variables inline, rather than in a separate statement.

### Do 
```	
var item = items.default(); 
var salesOrder = data.sales().salesOrders().createDefault();
var salesLine = salesOrder.addLine().setItem(item).setInventDims([warehouse]).setQuantity(10).save();
```
### Don't
```
InventTable item; 
AtlEntitySalesOrder salesOrder;
AtlEntitySaleOrderLine salesLine;
	
…
	
item = items.default(); 
salesOrder = data.sales().salesOrders().createDefault();
salesLine = salesOrder.addLine().setItem(item).setInventDims([warehouse]).setQuantity(10).save();
```
		   
### Justification

The advantage of using `var` is that you write less code, you don't have to remember exact type names, and the test logic isn't cluttered with unimportant information. Overall, the test code easier to read.

In the previous example it doesn't matter if `item` is of type `ItemId`, `InventlTable` or `AtlEntityInventItem`. The important information is that you are creating a sales line with the well-known default item. The exact types of the `salesOrder` and `salesLine` variables are not important. It's clear from the naming and usage what the contracts of their types are.
	
### Considerations 

Don't use type inference when you want compilation to fail if the return type of a method changes. 

Don't use type inference if you can't come up with meaningful variable or method names.

## Use entity instead of ID as method parameter

Well-known data methods, creator methods, and `init` methods usually return records or entities rather than IDs. We recommend that you use records or entities as method parameters.

### Do

```
var salesLine = salesOrder.addLine().setItem(item).save();
```

### Don't

```
var salesLine = salesOrder.addLine().setItemId(item.ItemId).save();
```

### Justification
The code is easier to read because it's not cluttered with unimportant technicalities.

### Considerations
If you only know the ID then use the method that takes ID as argument. 

## Use navigation node shortcuts
When automating a new domain area, introduce a base class that holds shortcuts to the most commonly used navigation objects in the area. 

For the warehouse management area there is a base class that is named `AtlWHSTestCase`. It contains shortcuts to `data.whs()`, `data.invent()`, `data.invent().items()`, `data.invent().units()`, and others. The shortcuts simplify your test code.

```
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

It also makes sense to introduce shortcuts that are common for many test methods within the same class.

### Do

```
class WHSMinMaxReplenishmentScenarioTest extends AtlWHSTestCase
…
    var item = items.default(); 
    var warehouse = invent.warehouses().default(); 
```

### Don't

```
class WHSMinMaxReplenishmentScenarioTest extends SysTestCase
…
    var item = data.invent().items().default(); 
    var warehouse = data.invent().warehouses().default(); 
```

### Consideration
You don't have to create a shortcut for every navigation node you need, but do consider making them for the ones that are commonly used.

