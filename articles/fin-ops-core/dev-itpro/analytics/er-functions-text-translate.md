---
# required metadata

title: TRANSLATE ER function
description: This topic provides information about how the TRANSLATE Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 04/02/2020
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

The `TRANSLATE` function returns a *String* value that contains the result of the character replacement of specified text in characters of another provided set.

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

## Usage notes

The `TRANSLATE` function replaces one character at a time. The function replaces the first character of the `text` argument with the first character of the `pattern` argument and then the second character and follows the same flow until finished. When a character from the `text` and `pattern` arguments match, it is replaced by a character from the `replacement` argument that is located in the same position as the character from the `pattern` argument. If a character appears multiple times in the `pattern` argument, the `replacement` argument mapping that corresponds to the first occurrence of this character is used.

## Example 1

`TRANSLATE ("abcdef", "cd", "GH")` replaces the **"c"** character of the specified  **“abcdef”** text with the **"G"** character of the `replacement` text due to the following:
-	The **"c"** character is presented in the `pattern` text in the first position.
-	The first position of the `replacement` text contains the **"G"** character.

## Example 2

`TRANSLATE ("abcdef", "ccd", "GH")` returns **"abGdef"**.

## Example 3

`TRANSLATE ("abccba", "abc", "123")` returns **"123321"**.

## Additional resources

[Text functions](er-functions-category-text.md)
