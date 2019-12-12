---
# required metadata

title: AND ER function
description: This topic provides information about how the AND ER function is used.
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

# <a name="AND">AND Function</a>

[!include [banner](../includes/banner.md)]

The `AND` function returns a *Boolean* **TRUE** if all of the specified conditions are true. Otherwise, it returns a *Boolean* **FALSE**.

## Syntax

```
AND (condition 1 [, condition 2, …])
```

## Arguments

`condition 1` : *Boolean*

A valid conditional expression to be tested. One argument is mandatory.

`condition N` : *Boolean*

A valid conditional expression to be tested. Other arguments are optional.

## Returns

*Boolean*

The result *Boolean* value.

## Usage notes

In arguments of the logical functions, you can use data source references, numeric and text values, boolean values, comparison operators, and other ER functions. However, all arguments must evaluate to the *Boolean* values of
**TRUE** or **FALSE**.

## Example

`AND (1=1, "a"="a")` returns TRUE.

`AND (1=2, "a"="a")` returns FALSE.

## Additional resources

[Logical functions](er-functions-category-logical.md)
