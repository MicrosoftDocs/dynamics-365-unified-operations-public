---
title: Queries in the Acceptance test library
description: Learn about how to use queries in the Acceptance test library, including an overview on naming conventions, implementation, and code examples.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: article
ms.date: 03/16/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-03-27
ms.dyn365.ops.version: App Update 10.0.2
---

# Queries in the Acceptance test library

[!include [banner](../includes/banner.md)]

A query class provides fluent APIs that you use to find an instance of the corresponding entity based on various criteria. Use query classes in validation scenarios. Use them together with specifications.

## Naming convention

`AtlQuery<ModuleName><EntityNamePlural>`

In this naming convention:

- `<ModuleName>` is optional. Use the names of the modules on the main menu. Use a short version or an abbreviation to keep the test code brief.
- `<EntityNamePlural>` is the plural version of the entity name.

## Examples

```xpp
AtlQueryWHSLoadLines

AtlQueryInventTransferOrderLines
```

## Implementation

All query classes inherit from the `AtlQuery` class.

## Fluent setters

Query classes should provide fluent setter methods to specify ranges for the query.

### Example

```xpp
loadLine = data.whs().loadLines().query().forSalesOrder(salesOrder).single();
```

Queries include two types of fluent setter methods: `for` methods and `with` methods:

- **for** – Use these methods for filters in the query that act as parents in composition or aggregation relationships. For example, the sales lines query exposes a `for` method to filter sales lines for a specific sales order.
- **with** – Use these methods for all other ranges in the query.

### Naming convention

`for<QueryRangeName>`

`with<QueryRangeName>`

In this naming convention, `<QueryRangeName>` is the name of the field that the range applies to.

### Examples

```xpp
loadLine = data.whs().loadLines().query().forLoad(load).withInventQty(10).single();

transferLine = data.invent().transferOrderLines().query().forTransferOrder(transferOrder).withInventDims([batch1]).single();
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
