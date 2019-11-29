---
# required metadata

title: ORDERBY ER function
description: This topic explains how the ORDERBY ER function is used
author: NickSelin
manager: kfend
ms.date: 11/29/2019
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

# <a name="ORDERBY">ORDERBY Function</a>

[!include [banner](../includes/banner.md)]

The `ORDERBY` function returns the specified list as a *Record list* after it has been sorted according to the specified arguments. These arguments can be defined as expressions.

## Syntax

```
ORDERBY (list , expression 1 [, expression 2, … , expression N])
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

`expression 1` : *Field*

A valid path to a field of a data source that is referred by using the first argument of the called function. The referred field must be a field of the primitive data type. This argument is mandatory.

`expression N` : *Field*

A valid path to a field of a data source that is referred by using the first argument of the called function. The referred field must be a field of the primitive data type. These arguments are optional.

## Returns

*Record list*

The result list of records.

## Example 1

If you enter the data source **DS** of the `Calculated field` type and it contains the expression `SPLIT ("C|B|A", “|”)`, the expression `FIRST( ORDERBY( DS, DS. Value)).Value` returns the text value, “A”.

## Example 2

If **Vendor** is configured as an ER data source that refers to the **VendTable** table, `ORDERBY (Vendors, Vendors.'name()')` expression returns a list of vendors that is sorted by name in ascending order.

## Additional resources

[List functions](er-functions-category-list.md)
