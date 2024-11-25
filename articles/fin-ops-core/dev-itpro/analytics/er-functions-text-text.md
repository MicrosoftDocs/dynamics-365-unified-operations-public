---
title: TEXT ER function
description: Learn about how the TEXT Electronic reporting (ER) function is used, including syntax strings, arguments, return values, usage notes, and examples.
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

# TEXT ER function

[!include [banner](../includes/banner.md)]

The `TEXT` function returns the specified number as a *String* value after it has been converted to a text string that is formatted according to the server locale settings of the current application instance.

## Syntax

```vb
TEXT (number)
```

## Arguments

`number`: *Integer* or *Real*

A number that must be converted to a text string.

## Return values

*String*

The resulting text value.

## Usage notes

For values of the *Real* type, the string conversion is limited to two decimal places.

## Example

If the server locale of the Microsoft Dynamics 365 Finance instance is defined as **EN-US**, `TEXT (NOW ())` returns the current Finance session date, December 17, 2015, as the text string **"12/17/2015 07:59:23 AM"**. `TEXT (1/3)` returns **"0.33"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
