---
# required metadata

title: ROUNDAMOUNT ER function
description: This topic provides information about how the ROUNDAMOUNT Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# <a name="ROUNDAMOUNT">ROUNDAMOUNT ER function</a>

[!include [banner](../includes/banner.md)]

The `ROUNDAMOUNT` function returns a *Real* value that represents the result of rounding the specified amount to the specified number of decimal places according to the specified rounding rule.

## Syntax

```
ROUNDAMOUNT (number, decimals, round rule)
```

## Arguments

`number`: *Int* or *Real*

A numeric value that must be rounded.

`decimals`: *Int*

A numeric value that specifies the number of decimal places to round the specified number to.

`round rule`: *Enum value*

An enumeration value of the **RoundOffType** enumeration that defines the rounding rule.

## Return values

*Real*

The resulting numeric value.

## Example

If the **model.RoundOff** parameter is set to **RoundOffType.Downward**, `ROUNDAMOUNT (1000.787, 2, model.RoundOff)` returns the value **1000.78**. 

If the **model.RoundOff** parameter is set to either **RoundOffType.Normal** or **RoundOffType.Rounding-up**, `ROUNDAMOUNT (1000.787, 2, model.RoundOff)` returns the value **1000.79**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
