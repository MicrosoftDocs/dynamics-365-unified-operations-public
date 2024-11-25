---
title: NOT ER function
description: Learn about how the NOT Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 12/17/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# NOT ER function

[!include [banner](../includes/banner.md)]

The `NOT` function returns the reversed logical value of the specified condition as a *Boolean* value.

## Syntax

```vb
NOT (condition)
```

## Arguments

`condition`: *Boolean*

A valid conditional expression that must be reversed.

## Return values

*Boolean*

The resulting *Boolean* value.

## Example

`NOT (TRUE)` returns **FALSE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
