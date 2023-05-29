---
title: ISEMPTY ER function
description: This article provides information about how the ISEMPTY Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/12/2019
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# ISEMPTY ER function

[!include [banner](../includes/banner.md)]

The `ISEMPTY` function returns a *Boolean* value of **TRUE** if the specified list contains no records. Otherwise, it returns a *Boolean* value of **FALSE**.

## Syntax

```vb
ISEMPTY (list)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

## Return values

*Boolean*

The resulting *Boolean* value.

## Example 1

If you enter data source **DS** of the *Calculated field* type, and it contains the expression `SPLIT ("A|B|C", "|")`, the expression `ISEMPTY(DS)` returns **FALSE**.

## Example 2

The expression `ISEMPTY (SPLIT ("",1))` returns **TRUE**.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
