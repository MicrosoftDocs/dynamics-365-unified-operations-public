---
# required metadata

title: Queries in the acceptance test library
description: This topic provides information about using queries in the acceptance test library.
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

# Queries in the acceptance test library
[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

A query class provides fluent APIs for finding an instance of the corresponding entity based on various criteria. Query classes are often used in validation scenarios, usually together with specifications.

## Naming convention
`AtlQuery<ModuleName><EntityNamePlural>`

Where:
- ModuleName (optional) is based on the names of the modules in main menu. However a short version or an abbreviation should be used to support the brevity of test code.
- EntityNamePlural is the plural version of the entity name.

## Examples
```
	AtlQueryWHSLoadLines
	AtlQueryInventTransferOrderLines
```

## Implementation
Query classes inherit from the `AtlQuery` class which is common for all queries.

## Fluent setters
Query classes should provide fluent setter methods to specify ranges for the query.

### Example
```
loadLine = data.whs().loadLines().query().forSalesOrder(salesOrder).single();
```

Queries allow two types of fluent setter methods, `for` and `with`:

- `for` methods: These methods are used for those filters of the query that act as parents of Composition or Aggregation relationships. For example, the sales lines query would expose a `for` method for filtering sales lines for a specific sales order.
- `with` methods: These methods are used for all other ranges of the query.

### Naming convention
`for<QueryRangeName>`

`with<QueryRangeName>`

QueryRangeName is the name of the field the range is applied on.

### Examples
```
loadLine = data.whs().loadLines().query().forLoad(load).withInventQty(10).single();

transferLine = data.invent().transferOrderLines().query().forTransferOrder(transferOrder).withInventDims([batch1]).single();
```
