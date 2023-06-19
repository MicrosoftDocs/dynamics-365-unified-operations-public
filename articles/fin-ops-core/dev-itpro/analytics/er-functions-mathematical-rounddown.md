---
title: ROUNDDOWN ER function
description: This article provides information about how the ROUNDDOWN Electronic reporting (ER) function is used.
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

# ROUNDDOWN ER function

[!include [banner](../includes/banner.md)]

The `ROUNDDOWN` function returns the specified number as a *Real* value after it has been rounded down to the specified number of decimal places.

## Syntax

```vb
ROUNDDOWN (number, decimals)
```

## Arguments

`number`: *Real*

A numeric value that must be rounded down.

`decimals`: *Integer*

A numeric value that represents the number of decimal places.

## Return values

*Real*

The resulting numeric value.

## Usage notes

This function behaves like [ROUND](er-functions-mathematical-round.md), but it always rounds the specified number down (toward zero).

## Example 1

`ROUNDDOWN (1200.767, 2)` rounds down to two decimal places and returns **1200.76**. 

## Example 2

`ROUNDDOWN (1700.767, -3)` rounds down to the nearest multiple of 1,000 and returns **1000**.

## Additional resources

[Mathematical functions](er-functions-category-mathematical.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
