---
# required metadata

title: Writing extensible tables
description: This article describes extensible tables.
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

Tables have a rich extension model, allowing extenders to add fields, field groups, indexes, relations, methods and more.

## Unique indices
Unique indices cannot be changed by an extension. Unique indices define a table constraint, and often also the key of the rows in the tables.  It is not allowed to change unique indices as it would change the nature of the table with a high risk of causing logical conflicts with future versions of the solution defining the table, or other solutions consuming the table.

Therefore avoid unique indices that are likely to be changed or likely to be requested changed in the future.  For example, do not create a unique index on product dimension [Color, Size, Style, Config]. Instead create a unique index on distinct product variant. This way the index doesn't have to change if new product dimensions are added.

If an extensible uniqueness constraint on multiple columns is required, consider creating a hash of the column's values. See the ```NumberSequenceScope``` table for an example of this.

## Data events
Table have a large number of data events predefined, that automatically are raised.  These are great extension points you provide by free. 

Avoid calling ```doInsert()```, ```doUpdate()``` and ```doDelete()``` as this prevents the data events from being raised, and makes your table harder to extend. Instead call ```insert()```, ```update()``` and ```delete()```.

## Field groups
Always use field groups to group related fields and build forms and reports.  Doing this consistently enables extension to surface additional fields in forms and reports by simply extending the field group.
