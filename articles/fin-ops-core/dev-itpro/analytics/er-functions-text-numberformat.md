---
# required metadata

title: NUMBERFORMAT ER function
description: This topic provides information about how the NUMBERFORMAT Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/10/2019
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

# <a name="NUMBERFORMAT">NUMBERFORMAT ER function</a>

[!include [banner](../includes/banner.md)]

The `NUMBERFORMAT` function returns a *String* value that presents the specified number in the specified format and in an optionally specified [culture](https://docs.microsoft.com/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes). For information about the supported formats, see [standard](https://msdn.microsoft.com/library/dwhawy9k(v=vs.110).aspx) and
[custom](https://msdn.microsoft.com/library/0c899ak8(v=vs.110).aspx).

## Syntax 1

```ER expression
NUMBERFORMAT (number, format)
```

## Syntax 2

```ER expression
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
