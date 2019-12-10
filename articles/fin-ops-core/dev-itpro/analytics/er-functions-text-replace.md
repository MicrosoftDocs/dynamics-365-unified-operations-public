---
# required metadata

title: REPLACE ER function
description: This topic provides information about how the REPLACE ER function is used.
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

# <a name="REPLACE">REPLACE Function</a>

[!include [banner](../includes/banner.md)]

The `REPLACE` function returns a *String* value of the specified text replacing all or part of this text string with another string.

## Syntax

```
REPLACE (text, pattern, replacement, regular expression flag)
```

## Arguments

`text` : *String*

A valid path to a data source of the *String* type.

`pattern` : *String*

When the regular expression flag is **FALSE**, contains a text using for replacement.

When the regular expression flag is **TRUE**, contains the regular expression sequence of characters that defines a search pattern as well as a replacement text.

`replacement` : *String*

When the regular expression flag is **FALSE**, contains a text that must be replaced.

When the regular expression flag is **TRUE**, not used.

`regular expression flag` : *Boolean*

A *Boolean* value to indicate whether a regular expression is used to perform replacement.

## Returns

*String*

The result text value.

## Usage notes

When the specified **regular expression flag** parameter is **TRUE**, return the specified string after it has been modified by applying the regular expression that is specified as the **pattern** argument for this function. This expression is used to find characters that must be replaced.

Characters of the specified **replacement** argument are used to replace characters that are found. When the specified **regular expression flag** parameter is **FALSE**, this function behaves like [TRANSLATE](er-functions-text-translate.md).

## Example 1

`REPLACE ("+1 923 456 4971", "[^0-9]", "", true)` applies a regular expression that removes all non-numeric symbols, and returns **"19234564971"**. 

## Example 2

`REPLACE ("abcdef", "cd", "GH", false)` replaces the pattern **"cd"** with the string **"GH"** and returns **"abGHef"**.

## Additional resources

[Text functions](er-functions-category-text.md)
