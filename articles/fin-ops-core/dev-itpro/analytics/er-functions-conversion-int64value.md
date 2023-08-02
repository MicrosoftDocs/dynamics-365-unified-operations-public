---
title: INT64VALUE ER function
description: This article provides information about how the INT64VALUE Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/05/2019
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

# INT64VALUE ER function

[!include [banner](../includes/banner.md)]

The `INT64VALUE` function returns an *Int64* value that represents the specified string.

## Syntax 1

```vb
INT64VALUE (text)
```

## Syntax 2

```vb
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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
