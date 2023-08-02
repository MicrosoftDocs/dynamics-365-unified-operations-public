---
title: NUMBERVALUE ER function
description: This article provides information about how the NUMBERVALUE Electronic reporting (ER) function is used.
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

# NUMBERVALUE ER function

[!include [banner](../includes/banner.md)]

The `NUMBERVALUE` function returns a *Real* value that is converted from the specified *String* value. During the conversion, the specified decimal and digit grouping separators are considered.

## Syntax

```vb
NUMBERVALUE (text, decimal separator, digit grouping separator)
```

## Arguments

`text`: *String*

A text value that must be converted to a *Real* number.

`decimal separator`: String

A decimal separator. It's used to separate the integer and fractional parts of a decimal number.

`digit grouping separator`: *String*

A digit grouping separator. It's used as the thousands separator.

## Return values

*Real*

The resulting numeric value.

## Example

`NUMBERVALUE( "1 234,56", ",", " ")` returns **1234.56**.

## Additional resources

[Type conversion functions](er-functions-category-type-conversion.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
