---
title: Write extensible tables
description: This topic provides information about how to write extensible tables.
author: MichaelFruergaardPontoppidan
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.technology: 


# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible tables
[!include [banner](../includes/banner.md)]

Tables have a rich extension model that lets extenders add fields, field groups, indexes, relations, methods, and more.

## Unique indexes
Unique indexes can't be changed by an extension. Unique indexes define a table constraint, and they often also define the key of the rows in the tables. You aren't allowed to change unique indexes, because such changes change the nature of the table. Therefore, there is a high risk that the changes will cause logical conflicts with future versions of the solution that defines the table, or with other solutions that consume the table.

Avoid unique indexes that are likely to be changed either now or in the future. For example, don't create a unique index on product dimensions such as color, size, style, and configuration. Instead, create a unique index on a distinct product variant, so that the index doesn't have to be changed if new product dimensions are added.

If you require an extensible uniqueness constraint on multiple columns, consider creating a hash of the column's values. For an example, see the NumberSequenceScope table.

## Data events
Tables have many predefined data events that are automatically raised.

Avoid calling **doInsert()**, **doUpdate()**, and **doDelete()**. These methods prevent the data events from being raised and make your table harder to extend. Instead, call **insert()**, **update()**, and **delete()**.

## Field groups
Always use field groups to group related fields, and to build forms and reports. By consistently using this approach, you enable the extension to surface additional fields in forms and on reports by extending the field group.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]