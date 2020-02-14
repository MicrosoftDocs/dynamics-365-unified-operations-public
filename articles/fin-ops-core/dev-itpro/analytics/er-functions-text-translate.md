---
# required metadata

title: TRANSLATE ER function
description: This topic provides information about how the TRANSLATE Electronic reporting (ER) function is used.
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

# <a name="TRANSLATE">TRANSLATE ER function</a>

[!include [banner](../includes/banner.md)]

The `TRANSLATE` function returns the specified text string as a *String* value after all or part of it has been replaced with another string.

## Syntax

```vb
TRANSLATE (text , pattern, replacement)
```

## Arguments

`text`: *String*

The valid path of a data source of the *String* type.

`pattern`: *String*

The text that must be replaced.

`replacement`: *String*

The text to use as a replacement.

## Return values

*String*

The resulting text value.

## Example

`TRANSLATE ("abcdef", "cd", "GH")` replaces the pattern **"cd"** with the string **"GH"** and returns **"abGHef"**.

## Additional resources

[Text functions](er-functions-category-text.md)
