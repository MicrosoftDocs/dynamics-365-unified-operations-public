---
# required metadata

title: TRANSLATE ER function
description: This topic explains how the TRANSLATE ER function is used
author: NickSelin
manager: kfend
ms.date: 11/29/2019
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

# <a name="TRANSLATE">TRANSLATE Function</a>

[!include [banner](../includes/banner.md)]

The `TRANSLATE` function returns a *String* value of the specified text replacing all or part of this text string with another string.

## Syntax

```
TRANSLATE (text , pattern, replacement)
```

## Arguments

`text` : *String*

A valid path to a data source of the *String* type.

`pattern` : *String*

A text that must be replaced.

`replacement` : *String*

A text using for replacement.

## Returns

*String*

The result text value.

## Example

`TRANSLATE ("abcdef", "cd", "GH")` replaces the pattern **"cd"** with the string **"GH"** and returns **"abGHef"**.

## Additional resources

[Text functions](er-functions-category-text.md)
