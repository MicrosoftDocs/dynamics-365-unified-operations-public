---
# required metadata

title: LEFT ER function
description: This topic provides information about how the LEFT ER function is used.
author: NickSelin
manager: kfend
ms.date: 12/11/2019
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

# <a name="LEFT">LEFT Function</a>

[!include [banner](../includes/banner.md)]

The `LEFT` function returns a *String* value as the specified number of characters from the start of the specified string.

## Syntax

```
LEFT (text, number)
```

## Arguments

`text` : *String*

A *String* value of the original text.

`number` : *Integer*

The number of characters to be returned from the start of the original text.

## Returns

*String*

The result text value.

## Example

`LEFT ("Sample", 3)` returns "Sam".

## Additional resources

[Text functions](er-functions-category-text.md)
