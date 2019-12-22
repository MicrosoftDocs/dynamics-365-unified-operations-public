---
# required metadata

title: INTVALUE ER function
description: This topic provides information about how the INTVALUE Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/05/2019
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

# <a name="INTVALUE">INTVALUE ER function</a>

[!include [banner](../includes/banner.md)]

The `INTVALUE` function returns an *Int* value that represents the specified string.

## Syntax 1

```
INTVALUE (text)
```

## Syntax 2

```
INTVALUE (number)
```

## Arguments

`text`: *String*

A text value that must be converted to an *Int* number.

`number`: *Real* or *Integer*

A numeric *Real* or *Integer* value that must be converted to an *Int* number.

## Return values

*Int*

The resulting numeric value.

## Usage notes

Any decimal places are truncated.

## Example 1

`INTVALUE ("100.77")` returns the *Int* value **100**.

## Example 2

`INTVALUE (-100.77)` returns the *Int* value **-100**.

## Additional resources

[Type conversion functions](er-functions-category-type-conversion.md)
