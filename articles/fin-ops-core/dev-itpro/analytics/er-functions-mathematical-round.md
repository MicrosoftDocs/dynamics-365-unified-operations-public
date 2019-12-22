---
# required metadata

title: ROUND ER function
description: This topic provides information about how the ROUND Electronic reporting (ER) function is used.
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

# <a name="ROUND">ROUND ER function</a>

[!include [banner](../includes/banner.md)]

The `ROUND` function returns the specified number as a *Real* value after it has been rounded to the specified number of decimal places.

## Syntax

```
ROUND (number, decimals)
```

## Arguments

`number`: *Real*

A numeric value that must be rounded.

`decimals`: *Integer*

A numeric value that represents the number of decimal places.

## Return values

*Real*

The resulting numeric value.

## Usage notes

If the value of the `decimals` argument is more than 0 (zero), the specified number is rounded to that many decimal places.

If the value of the `decimals` argument is **0** (zero), the specified number is rounded to the nearest integer.

If the value of the `decimals` argument is less than 0 (zero), the specified number is rounded to the left of the decimal point.

## Example 1

`ROUND (1200.767, 2)` rounds to two decimal places and returns **1200.77**.

## Example 2

`ROUND (1200.767, -3)` rounds to the nearest multiple of 1,000 and returns **1000**.

## Additional resources

[Mathematical functions](er-functions-category-mathematical.md)
