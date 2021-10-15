---
# required metadata

title: ABS ER function
description: This topic provides information about how the ABS Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 12/17/2019
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

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