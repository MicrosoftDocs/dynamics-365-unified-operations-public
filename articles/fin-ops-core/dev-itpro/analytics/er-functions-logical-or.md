---
# required metadata

title: OR ER function
description: This topic provides information about how the OR ER function is used.
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

# <a name="OR">OR Function</a>

[!include [banner](../includes/banner.md)]

The `OR` function returns a *Boolean* **FALSE** if all of the specified conditions are false. Return a *Boolean* **TRUE** if any specified condition is true.

## Syntax

```
OR (condition 1[, condition 2, … , condition N])
```

## Arguments

`condition 1` : *Boolean*

A valid conditional expression to be tested. This argument is mandatory.

`condition N` : *Boolean*

A valid conditional expression to be tested. Other arguments are optional.

## Returns

*Boolean*

The result *Boolean* value.

## Example

`OR (1=2, "a"="a")` returns **TRUE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
