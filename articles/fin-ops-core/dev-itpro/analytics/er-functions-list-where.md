---
# required metadata

title: WHERE ER function
description: This topic explains how the WHERE ER function is used
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

# <a name="WHERE">WHERE Function</a>

[!include [banner](../includes/banner.md)]

The `WHERE` function returns the specified list as a *Record list* after it has been filtered according to the specified condition.

## Syntax

```
WHERE (list, condition)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

`condition` : *Boolean*

A valid conditional expression to filter records of a given list.

## Returns

*Record list*

The result list of records.

## Usage notes

This function differs from the [FILTER](er-functions-list-filter.md) function, because the specified condition is applied to any ER data source of the *Record
list* type in memory.

When the configured arguments of this functions (list and condition) allow to translate this request to the direct SQL call, the warning is thrown at design time informing that from the performance improvement perspective it would be
better to use the
[FILTER](file:///C:\Users\nselin\Documents\Projects\Ger\Content\Formula%20%20designer%20-%20restructuring\Formula%20designer%20(updated)\Formula%20language%20(new)\Category%20-%20list%20(new)\er-functions-list-filter.md)
function instead of `WHERE`.

## Example 1

If **Vendor** is configured as an ER data source that refers to the **VendTable** table, `WHERE (Vendors, Vendors.VendGroup = "40")` returns a list of just the vendors that belong to vendor group 40.

## Example 2

If you enter the data source **DS** of the `Calculated field` type and it contains the expression `SPLIT ("A|B|C", “|”)`, the `WHERE( DS, DS.Value = “B”)` expression returns a list of just one record that contains the text “B” in the **Value** field.

## Additional resources

[List functions](er-functions-category-list.md)
