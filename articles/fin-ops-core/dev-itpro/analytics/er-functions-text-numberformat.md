---
title: NUMBERFORMAT ER function
description: This article provides information about how the NUMBERFORMAT Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/10/2019
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

# NUMBERFORMAT ER function

[!include [banner](../includes/banner.md)]

The `NUMBERFORMAT` function returns a *String* value that presents the specified number in the specified format and in an optionally specified [culture](/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes). For information about the supported formats, see [standard](/dotnet/standard/base-types/standard-numeric-format-strings) and
[custom](/dotnet/standard/base-types/custom-numeric-format-strings).

## Syntax 1

```vb
NUMBERFORMAT (number, format)
```

## Syntax 2

```vb
NUMBERFORMAT (number, format, culture)
```

## Arguments

`number`: *Integer* or *Real*

A numeric value that specifies the number that must be formatted.

`format` : *String*

A *String* value that represents the format.

`culture`: *String*

A *String* value that represents the culture to use for formatting.

## Return values

*String*

The resulting text value.

## Usage notes

If the culture isn't defined as an argument of the called function, the context that this function is run in determines the culture that is used to format numbers.

## Example 1

For the **EN-US** culture, `NUMBERFORMAT (0.45, "p")` returns **"45.00 %"**, and `NUMBERFORMAT (10.45, "#")` returns **"10"**.

## Example 2

`NUMBERFORMAT (10/3, "F2", "de")` returns **3,33**, whereas `NUMBERFORMAT (10/3, "F2", "en-us")` returns **3.33**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
