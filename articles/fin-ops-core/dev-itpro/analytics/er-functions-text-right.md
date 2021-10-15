---
# required metadata

title: RIGHT ER function
description: This topic provides information about how the RIGHT Electronic reporting (ER) function is used.
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

# RIGHT ER function

[!include [banner](../includes/banner.md)]

The `RIGHT` function returns a *String* value that presents the specified number of characters from the end of the specified string.

## Syntax

```vb
RIGHT (text, number)
```

## Arguments

`text`: *String*

A *String* value that represents the original text.

`number`: *Integer*

The number of characters that must be returned from the end of the original text.

## Return values

*String*

The resulting text value.

## Example

`RIGHT ("Sample", 3)` returns **"ple"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]