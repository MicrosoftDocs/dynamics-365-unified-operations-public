---
# required metadata

title: CONCATENATE ER function
description: This topic provides information about how the CONCATENATE Electronic reporting (ER) function is used
author: NickSelin
ms.date: 12/12/2019
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

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