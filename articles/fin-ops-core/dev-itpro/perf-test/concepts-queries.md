---
title: Queries in the Acceptance test library
description: This topic provides information about how to use queries in the Acceptance test library.
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

# Queries in the Acceptance test library

[!include [banner](../includes/banner.md)]

A query class provides fluent application programming interfaces (APIs) that are used to find an instance of the corresponding entity, based on various criteria. Query classes are often used in validation scenarios. They are usually used together with specifications.

## Naming convention

`AtlQuery<ModuleName><EntityNamePlural>`

In this naming convention:

- `<ModuleName>` is optional and is based on the names of the modules on the main menu. However, a short version or an abbreviation should be used to support brevity of test code.
- `<EntityNamePlural>` is the plural version of the entity name.

## Examples

```xpp
AtlQueryWHSLoadLines

AtlQueryInventTransferOrderLines
```

## Implementation

Query classes inherit from the `AtlQuery` class that is common to all queries.

## Fluent setters

Query classes should provide fluent setter methods to specify ranges for the query.

### Example

```xpp
loadLine = data.whs().loadLines().query().forSalesOrder(salesOrder).single();
```

Queries allow for two types of fluent setter methods, `for` methods and `with` methods:

- **for** – These methods are used for filters of the query that act as parents of composition or aggregation relationships. For example, the sales lines query exposes a `for` method to filter sales lines for a specific sales order.
- **with** – These methods are used for all other ranges of the query.

### Naming convention

`for<QueryRangeName>`

`with<QueryRangeName>`

In this naming convention, `<QueryRangeName>` is the name of the field that the range is applied on.

### Examples

```xpp
loadLine = data.whs().loadLines().query().forLoad(load).withInventQty(10).single();

transferLine = data.invent().transferOrderLines().query().forTransferOrder(transferOrder).withInventDims([batch1]).single();
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]