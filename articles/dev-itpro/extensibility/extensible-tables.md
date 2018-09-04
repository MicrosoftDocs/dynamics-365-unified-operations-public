---
# required metadata

title: Writing extensible tables
description: This article provides information about writing extensible tables.
author: mfp
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
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Tables

Tables have a rich extension model which allows extenders to add fields, field groups, indexes, relations, methods, and more.

## Unique indices
Unique indices can't be changed by an extension. Unique indices define a table constraint, and often also the key of the rows in the tables. Changing unique indices is not allowed because it would change the nature of the table with a high risk of causing logical conflicts with future versions of the solution that defines the table, or other solutions that consume the table.

Avoid unique indices that are likely to be changed either now or in the future. For example, don't create a unique index on product dimensions including color, size, style, and config. Instead, create a unique index on a distinct product variant so that the index doesn't have to change if new product dimensions are added.

If an extensible uniqueness constraint on multiple columns is required, consider creating a hash of the column's values. See the ```NumberSequenceScope``` table for an example of this.

## Data events
Tables have a large number of data events that are predefined and automatically raised. 

Avoid calling ```doInsert()```, ```doUpdate()``` and ```doDelete()``` because they prevents the data events from being raised and make your table harder to extend. Instead, call ```insert()```, ```update()```, and ```delete()```.

## Field groups
Always use field groups to group related fields and to build forms and reports. Doing this consistently enables the extension to surface additional fields in forms and reports by extending the field group.
