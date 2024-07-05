---
title: INTVALUE ER function
description: Learn about how the INTVALUE Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 12/05/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# INTVALUE ER function

[!include [banner](../includes/banner.md)]

The `INTVALUE` function returns an *Int* value that represents the specified string.

## Syntax 1

```vb
INTVALUE (text)
```

## Syntax 2

```vb
INTVALUE (number)
```

## Arguments

`text`: *String*

A text value that must be converted to an *Int* number.

`number`: *Real* or *Integer*

A numeric *Real* or *Integer* value that must be converted to an *Int* number.

## Return values

*Int*

The resulting numeric value.

## Usage notes

Any decimal places are truncated.

## Example 1

`INTVALUE ("100.77")` returns the *Int* value **100**.

## Example 2

`INTVALUE (-100.77)` returns the *Int* value **-100**.

## Additional resources

[Type conversion functions](er-functions-category-type-conversion.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
