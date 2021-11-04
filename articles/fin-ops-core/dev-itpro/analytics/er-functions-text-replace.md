---
# required metadata

title: REPLACE ER function
description: This topic provides information about how the REPLACE Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 04/02/2020
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

# REPLACE ER function

[!include [banner](../includes/banner.md)]

The `REPLACE` function returns the specified text string as a *String* value after all or part of it has been replaced with another string.

## Syntax

```vb
REPLACE (text, pattern, replacement, regular expression flag)
```

## Arguments

`text`: *String*

The valid path of a data source of the *String* type.

`pattern`: *String*

If the `regular expression flag` argument is **FALSE**, this argument contains the text that must be replaced.

If the `regular expression flag` argument is **TRUE**, this argument contains a regular expression that defines both a search pattern and the replacement text.

`replacement`: *String*

If the `regular expression flag` argument is **FALSE**, this argument contains the text to use as a replacement.

If the `regular expression flag` argument is **TRUE**, this argument isn't used.

`regular expression flag`: *Boolean*

A *Boolean* value that indicates whether a regular expression is used to do the replacement.

## Return values

*String*

The resulting text value.

## Usage notes

If the `regular expression flag` argument is **TRUE**, this function returns the specified string after it has been changed by applying the regular expression that is specified by the `pattern` argument. The regular expression is used to find the characters that must be replaced.

If the `regular expression flag` argument is **FALSE**, this function returns the specified string after the set of characters that are defined in the `pattern` argument have been replaced by characters of the `replacement` argument. 

## Example 1

`REPLACE ("+1 923 456 4971", "[^0-9]", "", true)` applies a regular expression that removes all non-numeric symbols, and it returns **"19234564971"**. 

## Example 2

`REPLACE ("abcdef", "cd", "GH", false)` replaces the pattern **"cd"** with the string **"GH"** and returns **"abGHef"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]