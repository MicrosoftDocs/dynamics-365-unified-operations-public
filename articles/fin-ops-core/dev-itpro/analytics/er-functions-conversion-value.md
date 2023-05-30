---
title: VALUE ER function
description: This article provides information about how the VALUE Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/05/2019
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

# VALUE ER function

[!include [banner](../includes/banner.md)]

The `VALUE` function returns a *Real* value that is converted from the specified string.

## Syntax

```vb
VALUE (text)
```

## Arguments

`text`: *String*

A string value that must be converted to a numeric value.

## Return values

*Real*

The resulting numeric value.

## Usage notes

Commas and dot characters (.) are considered decimal separators, and a leading hyphen (-) is used as a negative sign. An exception is thrown at runtime if the specified string contains other non-numeric characters.

## Example 1

`VALUE ("1 234,56")` throws an exception.

## Example 2

`VALUE ("1234,56")` returns **1234.56**.

## Additional resources

[Type conversion functions](er-functions-category-type-conversion.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
