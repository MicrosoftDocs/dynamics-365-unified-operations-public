---
title: FIRST ER function
description: This article provides information about how the FIRST Electronic reporting (ER) function is used.
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

# FIRST ER function

[!include [banner](../includes/banner.md)]

The `FIRST` function returns the first record of the specified list as a *Container (record)* value, if that list isn't empty. If the list is empty, this function throws an exception.

## Syntax

```vb
FIRST (list)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

## Return values

*Container (record)*

The resulting record value.

## Example 1

The expression `FIRST(SPLIT("ABC",1)).Value` returns the text value **"A"**.

## Example 2

The expression `FIRST(SPLIT("",1)).Value` throws an exception at runtime.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
