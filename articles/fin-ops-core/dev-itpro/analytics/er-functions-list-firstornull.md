---
title: FIRSTORNULL ER function
description: This article explains how the FIRSTORNULL Electronic reporting (ER) function is used
author: kfend
ms.date: 11/29/2019
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

# FIRSTORNULL ER function

[!include [banner](../includes/banner.md)]

The `FIRSTORNULL` function returns the first record of the specified list as a *Container (record)* value, if that record isn't empty. If the record is empty, this function returns a null *Container (record)* value.

## Syntax

```vb
FIRSTORNULL (list)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

## Return values

*Container (record)*

The resulting record value.

## Example

The expression `FIRSTORNULL(SPLIT("",1)).Value` returns an empty string (**""**).

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
