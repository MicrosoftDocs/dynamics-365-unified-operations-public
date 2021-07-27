---
# required metadata

title: CHAR ER function
description: This topic provides information about how the CHAR Electronic reporting (ER) function is used.
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

# CHAR ER function

[!include [banner](../includes/banner.md)]

The `CHAR` function returns a *String* value that presents a single character that is referenced by the specified Unicode number.

## Syntax

```vb
CHAR (number)
```

## Arguments

`number`: *Integer*

A number that corresponds to an expected single character.

## Return values

*String*

The resulting text value.

## Usage notes

The string that this function returns depends on the encoding that is selected in the parent **FILE** format element. For a list of the supported encodings, see [Encoding class](/dotnet/api/system.text.encoding).

## Example

`CHAR (255)` returns **"ÿ"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]