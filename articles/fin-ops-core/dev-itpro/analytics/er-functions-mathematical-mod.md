---
title: MOD ER function
description: Learn about how the MOD Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
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

# MOD ER function

[!INCLUDE [banner](../../../includes/banner.md)]

The `MOD` function is available for Finance and Operations **10.0.49** and later.

The `MOD` function returns the remainder after a number is divided by another number. In other words, it returns the modulus of the specified numbers.

## Syntax

```vb
MOD (dividend, divisor)
```

## Arguments

`dividend`: *Real* or *Integer*

The dividend, or the number to be divided.

`divisor`: *Real* or *Integer*

The divisor, or the number by which `dividend` is divided.

## Return values

*Real* or *Integer*

The resulting numeric value.

## Example

`MOD (5, 2)` returns **1**.

## Example 2

`MOD (6.6, 3.1)` returns **0.4**.

## Additional resources
 
[Mathematical functions](er-functions-category-mathematical.md)
