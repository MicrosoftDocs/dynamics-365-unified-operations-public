---
# required metadata

title: NOT ER function
description: This topic provides information about how the NOT Electronic reporting (ER) function is used.
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

# <a name="NOT">NOT ER function</a>

[!include [banner](../includes/banner.md)]

The `NOT` function returns the reversed logical value of the specified condition as a *Boolean* value.

## Syntax

```vb
NOT (condition)
```

## Arguments

`condition`: *Boolean*

A valid conditional expression that must be reversed.

## Return values

*Boolean*

The resulting *Boolean* value.

## Example

`NOT (TRUE)` returns **FALSE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
