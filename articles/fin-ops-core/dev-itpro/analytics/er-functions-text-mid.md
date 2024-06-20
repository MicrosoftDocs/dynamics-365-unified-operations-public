---
title: MID ER function
description: Learn about how the MID Electronic reporting (ER) function is used, including syntax strings,a rguments, return values, usage notes, and examples.
author: kfend
ms.author: filatovm
ms.topic: conceptual
ms.date: 12/10/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# MID ER function

[!include [banner](../includes/banner.md)]

The `MID` function returns a *String* value that presents the specified number of characters from the specified string, starting at the specified position.

## Syntax

```vb
MID (text, starting position, number of characters)
```

## Arguments

`text`: *String*

A *String* value that specifies the text to return characters from.

`starting position`: *Integer*

An *Integer* value that specifies the position of the first character that must be returned from the specified text.

`number of characters`: *Integer*

An *Integer* value that specifies the number of characters that must be returned, starting at the specified starting position.

## Return values

*String*

The resulting text value.

## Usage notes

If the value of the `starting position` argument is less than 0 (zero), the characters that are returned are counted from the first position in the specified string.

If the value of the `starting position` argument exceeds length of the specified string, an empty string is returned.

## Example

`MID ("Sample", 2, 3)` returns **"amp"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
