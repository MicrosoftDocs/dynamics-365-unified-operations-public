---
title: CONCATENATE ER function
description: Learn about how the CONCATENATE Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: conceptual
ms.date: 12/12/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# CONCATENATE ER function

[!include [banner](../includes/banner.md)]

The `CONCATENATE` function returns all the specified text strings as a *String* value after they have been joined into one string.

## Syntax

```vb
CONCATENATE (text 1[, text 2, …, text N])
```

## Arguments

`text 1`: *String*

A reference to a data source of the *String* data type. This argument is required.

`text N`: *String*

A reference to a data source of the *String* data type. These additional arguments are optional.

## Return values

*String*

The resulting text value.

## Example

`CONCATENATE ("abc", "def")` returns **"abcdef"**.

## Usage notes

The expression `"abc" & "def"` also returns **"abcdef"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
