---
title: ROUNDAMOUNT ER function
description: This article provides information about how the ROUNDAMOUNT Electronic reporting (ER) function is used.
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

# ROUNDAMOUNT ER function

[!include [banner](../includes/banner.md)]

The `ROUNDAMOUNT` function returns a *Real* value as the result of the rounding of the specified number to the nearest multiple of another number according to the specified rounding rule.

## Syntax

```vb
ROUNDAMOUNT (number, decimals, round rule)
```

## Arguments

`number`: *Int* or *Real*

A numeric value that must be rounded.

`decimals`: *Int* or *Real*

The number that the value of the `number` parameter must be rounded to a multiple of.

`round rule`: *Enum value*

An enumeration value of the **RoundOffType** enumeration that defines the rounding rule. This enumeration offers the following values:

- Normal (Ordinary)
- Downward (RoundDown)
- Rounding-up (RoundUp)

## Return values

*Real*

The resulting numeric value is a multiple of the value specified by the `decimals` parameter and is closest to the value specified by the `number` parameter.

## Usage notes

When the `number` parameter is zero, this function always returns zero.

When the `decimals` parameter is zero, this function rounds to the default round-off value. When the `round rule` parameter is set to **RoundOffType.Ordinary**, the default round-off value is **0.01**. Otherwise, the default round-off value is **1.0**.

When the `round rule` parameter is set to **RoundOffType.Ordinary**, this function rounds to the nearest round-off amount.

When the `round rule` parameter is set to **RoundOffType.RoundDown**, this function rounds towards zero to the nearest round-off amount.

When the `round rule` parameter is set to **RoundOffType.RoundUp**, this function rounds away from zero to the nearest round-off amount.

When the `round rule` parameter is set to **RoundOffType.Ordinary**, this function behaves like the [MROUND](https://support.office.com/article/mround-function-c299c3b0-15a5-426d-aa4b-d2d5b3baf427) Excel function and the [ROUND](../dev-ref/xpp-math-run-time-functions.md#round) X++ function.

## Remarks

To round a numeric value to a specified number of decimal places, use the [ROUND](er-functions-mathematical-round.md) function.

## Example

If the **model.RoundOff** parameter is set to **RoundOffType.Ordinary**, `ROUNDAMOUNT (7.45, 1.05, model.RoundOff)` returns 7.35. 

If the **model.RoundOff** parameter is set to **RoundOffType.RoundDown**, `ROUNDAMOUNT (7.45, 1.05, model.RoundOff)` returns 7.35. 

If the **model.RoundOff** parameter is set to **RoundOffType.RoundUp**, `ROUNDAMOUNT (7.45, 1.05, model.RoundOff)` returns 8.4.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)

[Mathematical functions](er-functions-category-mathematical.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
