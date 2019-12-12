---
# required metadata

title: ISEMPTY ER function
description: This topic provides information about how the ISEMPTY ER function is used.
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

# <a name="ISEMPTY">ISEMPTY Function</a>

[!include [banner](../includes/banner.md)]

The `ISEMPTY` returns a *Boolean* **TRUE** if the specified list contains no records. Otherwise, returns a *Boolean* **FALSE**.

## Syntax

```
ISEMPTY (list)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

## Returns

*Boolean*

The result *Boolean* value.

## Example 1

If you enter the data source **DS** of the `Calculated field` type and it contains the expression `SPLIT ("A|B|C", “|”)`, the expression `ISEMPTY(DS)` returns **FALSE**.

## Example 2

The expression `ISEMPTY (SPLIT ("",1))` returns **TRUE**.

## Additional resources

[List functions](er-functions-category-list.md)
