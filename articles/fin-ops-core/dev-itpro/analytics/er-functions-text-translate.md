---
title: TRANSLATE ER function
description: This article provides information about how the TRANSLATE Electronic reporting (ER) function is used.
author: kfend
ms.date: 04/02/2020
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

# TRANSLATE ER function

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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
