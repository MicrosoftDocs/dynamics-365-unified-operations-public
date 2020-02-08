---
# required metadata

title: Acceptance test library FAQ
description: This topic provides answers to frequently asked questions about the Acceptance test library.
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
ms.reviewer: rhaertle
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

# Acceptance test library FAQ

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

## Which fluent prefix should I use: set, for, or with?

Depending on the class that you want to add a fluent method to, different rules might apply:

- [Entities](concepts-entities.md)
- [Creators](concepts-creators.md)
- [Commands](concepts-commands.md)
- [Queries](concepts-queries.md)
- [Specifications](concepts-specifications.md)

## Should I implement an entity or a creator class?

For most entities, the effort of creating an entity class is the same as the effort of creating a creator class. Therefore, the entity class should be created. However, in some cases, the process of creating an entity might not be straightforward. A good example is the Item entity. Because more than ten different tables make up the Item entity, it's hard to create the entity class. Because you will almost never have to update existing items in your test cases, it's OK if you just have a creator class, which is much easier to implement.

## Does the order of the chained fluent setters matter?

In most of the cases, the order of the chained fluent setters doesn't matter. However, be aware that defaulting occurs at the time of the call to the setter method. Therefore, a change in the order of the methods can produce different results. Here is an example for the sales line.

### Option 1

```xpp
salesLine.setQuantity(10).setUnitPrice(100).setAmount(2000).save()
```

This option produces a sales line where the amount == 2,000, because the amount is set last.
	
### Option 2

```xpp
salesLine.setAmount(2000).setQuantity(10).setUnitPrice(100).save()
```

This option produces a sales line where the amount == 1,000, because after you set the unit price, the amount is set to quantity × price by default.

## Can I use ATL for tests that run on the empty data set?

The Acceptance test library (ATL) can be used on the empty data set without issues. The automatic setup of prerequisites is done on demand. For example, prerequisites for invoice posting will be set up only during the first call to `salesOrder.postInvoice()`. For more information, see [Ensure](test-data-methods.md#ensure-methods).

`Ensure` methods can also be called in the `setUpTestCase` method to improve performance if more than one test in your test class must post invoices.

## Can I use ATL for unit tests?

ATL should be used mostly for data setup and validation in integration and component tests. However, in some cases, it's also used for unit tests.

### Why should I be cautious about using ATL in unit and component tests?

In some of the more complex entities, such as Sales order, all the business logic that is associated with the `modifiedField`, `insert`, and `update` events is called. Creation of invoice transactions, for example, is also done by running real invoice posting logic. Therefore, the performance of some operations will be slow. However, these issues don't occur for most of the entities that represent master data. Therefore, you should be able to use those entities in any type of test.

There should not be significant overhead if specifications and queries are used to do validation. These artifacts can also be used in unit tests.
