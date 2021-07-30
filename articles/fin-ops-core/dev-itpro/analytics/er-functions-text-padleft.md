---
# required metadata

title: PADLEFT ER function
description: This topic provides information about how the PADLEFT Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 12/10/2019
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

# PADLEFT ER function

[!include [banner](../includes/banner.md)]

The `PADLEFT` function returns a *String* value of the specified length, where the start of the specified string is padded with the specified characters.

## Syntax

```vb
PADLEFT (text, length, padding chars)
```

## Arguments

`text`: *String*

A *String* value that represents the original text.

`length`: *Integer*

An *Integer* value that represents the final number of characters in the padded string.

`padding chars`: *String*

The characters to use for padding.

## Return values

*String*

The resulting text value.

## Example

`PADLEFT ("1234", 10, "`&nbsp;`")` returns the text string **"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1234"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]