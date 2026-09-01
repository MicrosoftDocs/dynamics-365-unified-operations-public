---
title: DIV ER function
description: Learn about how the DIV Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: liza-golub
ms.author: egolub
ms.topic: article
ms.date: 04/13/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2026-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# DIV ER function

[!INCLUDE [banner](../../../includes/banner.md)]

The `DIV` function is available in Dynamics 365 Finance **10.0.49** and later.

The `DIV` function returns the integer division of two integers. The result is the quotient of the division of `dividend` by `divisor`, rounded down to the nearest integer.

## Syntax

```vb
DIV (dividend, divisor)
```

## Arguments

`dividend`: *Integer*

The dividend, or the number to be divided.

`divisor`: *Integer*

The divisor, or the number by which `dividend` is divided.

## Return values

*Integer*

The resulting numeric value.

## Example

`DIV (5, 2)` returns **2**.

## Additional resources
 
[Mathematical functions](er-functions-category-mathematical.md)

