---
# required metadata

title: AND ER function
description: This topic provides information about how the AND Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/12/2019
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

# <a name="AND">AND ER function</a>

[!include [banner](../includes/banner.md)]

The `AND` function returns a *Boolean* value of **TRUE** if all the specified conditions are true. Otherwise, it returns a *Boolean* value of **FALSE**.

## Syntax

```
AND (condition 1[, condition 2, …, condition N])
```

## Arguments

`condition 1`: *Boolean*

A valid conditional expression that must be tested. This argument is required.

`condition N`: *Boolean*

A valid conditional expression that must be tested. These additional arguments are optional.

## Return values

*Boolean*

The resulting *Boolean* value.

## Usage notes

In the arguments of logical functions, you can use data source references, numeric and text values, Boolean values, comparison operators, and other Electronic reporting (ER) functions. However, all the arguments must be evaluated to a *Boolean* value of **TRUE** or **FALSE**.

## Example

`AND (1=1, "a"="a")` returns **TRUE**.

`AND (1=2, "a"="a")` returns **FALSE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
