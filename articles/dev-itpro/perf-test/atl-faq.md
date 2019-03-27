---
# required metadata

title: FAQ - Acceptance test library 
description: This topic provides answers to frequently asked questions about the acceptance test library.
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

# FAQ: Acceptance test library

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

## Which of fluent prefix should I use? `set`, `for` or `with`

Depending on the class where you want to add a fluent method to, different rules may apply:

- [Entities](Concepts_Entities.md)
- [Creators](Concepts_Creators.md)
- [Commands](Concepts_Commands.md)
- [Queries](Concepts_Queries.md)
- [Specifications](Concepts_Specifications.md)

## Should I implement an Entity or a Creator class?
For most of the entities, the effort of creating an entity class is the same as creating a creator class so the entity class should be created. However in some cases, creating an entity may not be straightforward. A good example is the Item entity. There are more than ten different tables that comprise the Item entity which makes it hard to create the entity class. Because we almost never need to update existing items in our test cases, it's fine to just have a creator class which is much easier to implement.

## Does order of the chained fluent setters matter?
In most of the cases the order doesn't matter. However, it is important to know that currently defaulting is happening at the time of the call to the setter method. This means that changing the order of the methods can produce different results. The following is an example with the sales line. 

### Option 1
```
salesLine.setQuantity(10).setUnitPrice(100).setAmount(2000).save()
```
This will result in a sales line with amount == 2000 because it was set last.
	
### Option 2
```
salesLine.setAmount(2000).setQuantity(10).setUnitPrice(100).save()
```
This will result in a sales line with amount == 1000 because once you set unit price, amount is defaulted as Quantity * Price.

## Can I use the Acceptance test library (ATL) for tests that run on the empty data set?
ATL can be used on the empty data with no problem. The automatic prerequisite setup is done on demand. For example, prerequisites for invoice posting will only be set up during the first call to `salesOrder.postInvoice()`. For more information, see [Ensure](Concepts_TestDataMethods.md#EnsureMethods).

`Ensure` methods can also be called in the `setUpTestCase` method to improve performance if more than one test in your test class needs to post invoices.

## Can I use ATL for unit tests?
ATL should mostly be used for data setup and validation in Integration and Component tests. In some cases we are using ATL for unit tests as well.

### Why should you should be cautious about using ATL in unit/component tests? 
In some of the more complex entities like Sales order, we are calling all of the business logic that is associated with the `modifiedField`, `insert`, and `update` events. Creating invoice transactions, for example, is also done by executing real invoice posting logic. 
This means that performance of certain operations will be slow. 
Most of the entities that represent master data do not have these problems so you should be able to use them in any type of tests. 
There shouldn’t be any significant overhead in using specs and queries for performing validation. These artifacts can be used in unit tests as well.
