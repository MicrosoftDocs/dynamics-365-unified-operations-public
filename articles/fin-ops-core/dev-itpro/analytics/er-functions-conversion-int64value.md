---
# required metadata

title: INT64VALUE ER function
description: This topic provides information about how the INT64VALUE Electronic reporting (ER) function is used.
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

# <a name="INT64VALUE">INT64VALUE ER function</a>

[!include [banner](../includes/banner.md)]

The `INT64VALUE` function returns an *Int64* value that represents the specified string.

## Syntax 1

```
INT64VALUE (text)
```

## Syntax 2

```
INT64VALUE (number)
```

## Arguments

`text`: *String*

A text value that must be converted to an *Int64* number.

`number`: *Real* or *Integer*

A numeric *Real* or *Integer* value that must be converted to an *Int64* number.

## Return values

*Int64*

The resulting numeric value.

## Usage notes

Any decimal places are truncated.

## Example 1

`INT64VALUE ("22565422744")` returns the *Int64* value **22565422744**.

## Example 2

`INT64VALUE ( VALUE("22565422744.77"))` returns the *Int64* value **22565422744**.

## Additional resources

[Type conversion functions](er-functions-category-type-conversion.md)
