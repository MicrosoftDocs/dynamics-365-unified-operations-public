---
# required metadata

title: REVERSE ER function
description: This topic provides information about how the REVERSE ER function is used.
author: NickSelin
manager: kfend
ms.date: 12/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# <a name="REVERSE">REVERSE Function</a>

[!include [banner](../includes/banner.md)]

The `REVERSE` function returns the specified list as a *Record list* in reversed sort order.

## Syntax

```
REVERSE (list)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

## Returns

*Record list*

The result list of records.

## Example 1

If you enter the data source **DS** of the `Calculated field` type and it contains the expression `SPLIT ("C|B|A", “|”)`, the expression `FIRST( REVERSE( ORDERBY( DS, DS. Value))).Value` returns the text value, “C”.

## Example 2

If **Vendor** is configured as an ER data source that refers to the **VendTable** table, the `REVERSE (ORDERBY (Vendors, Vendors.'name()'))` expression returns a list of vendors that is sorted by name in descending order.

## Additional resources

[List functions](er-functions-category-list.md)
