---
title: ABS ER function
description: This article provides information about how the ABS Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/17/2019
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

# ABS ER function

[!include [banner](../includes/banner.md)]

The `ABS` function returns the absolute value (modulus) of the specified number as a *Real* value. In other words, it returns the number without its sign.

## Syntax

```vb
ABS (number)
```

## Arguments

`number`: *Real*

A numeric value that you want the modulus of.

## Return values

*Real*

The resulting numeric value.

## Example

`ABS (-1)` returns **1**.

## Additional resources

[Mathematical functions](er-functions-category-mathematical.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
