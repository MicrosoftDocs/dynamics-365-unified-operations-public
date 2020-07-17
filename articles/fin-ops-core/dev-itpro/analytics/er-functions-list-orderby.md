---
# required metadata

title: ORDERBY ER function
description: This topic provides information about how the ORDERBY Electronic reporting (ER) function is used.
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

# <a name="ORDERBY">ORDERBY ER function</a>

[!include [banner](../includes/banner.md)]

The `ORDERBY` function returns the specified list as a *Record list* value after it has been sorted according to the specified arguments. These arguments can be defined as expressions.

## Syntax

```vb
ORDERBY (list , expression 1[, expression 2, …, expression N])
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

`expression 1`: *Field*

The valid path of a field of the data source that is referenced by the `list` argument of the called function. The referenced field must be a field of the primitive data type. This argument is required.

`expression N`: *Field*

The valid path of a field of the data source that is referenced by the `list` argument of the called function. The referenced field must be a field of the primitive data type. These additional arguments are optional.

## Return values

*Record list*

The resulting list of records.

## Example 1

If you enter data source **DS** of the *Calculated field* type, and it contains the expression `SPLIT ("C|B|A", "|")`, the expression `FIRST( ORDERBY( DS, DS. Value)).Value` returns the text value **"A"**.

## Example 2

If **Vendor** is configured as an Electronic reporting (ER) data source that refers to the VendTable table, the expression `ORDERBY (Vendors, Vendors.'name()')` returns a list of vendors that is sorted by name in ascending order.

## Additional resources

[List functions](er-functions-category-list.md)
