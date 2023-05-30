---
title: POWER ER function
description: This article provides information about how the POWER Electronic reporting (ER) function is used.
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

# POWER ER function

[!include [banner](../includes/banner.md)]

The `POWER` function returns a *Real* value that represents the result of raising the specified positive number to the specified power.

## Syntax

```vb
POWER (number, power)
```

## Arguments

`number`: *Real* or *Integer*

A numeric value that must be raised to the specified power.

`power`: *Real* or *Integer*

A numeric value that represents the specific power.

## Return values

*Real*

The resulting numeric value.

## Example 1

`POWER (10, 2)` returns **100**.

## Example 2

`POWER (4, 0.5)` returns **2**.

## Additional resources

[Mathematical functions](er-functions-category-mathematical.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
