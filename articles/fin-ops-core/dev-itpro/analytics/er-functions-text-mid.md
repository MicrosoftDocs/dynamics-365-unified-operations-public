---
# required metadata

title: MID ER function
description: This topic provides information about how the MID ER function is used.
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

# <a name="MID">MID Function</a>

[!include [banner](../includes/banner.md)]

Starting at the specified string position, the `MID` function returns a *String* value of the specified number of characters from the specified string.

## Syntax

```
MID (text, starting position, number of characters)
```

## Arguments

`text` : *String*

A *String* value of the specified text.

`starting position` : *Integer*

An *Integer* that specifies the position of the first character that must be returned.

`number of characters` : *Integer*

An *Integer* that specifies the number of characters, beginning with the specified starting position, to be returned from the specified text.

## Returns

*String*

The result text value.

## Usage notes

If the value of the starting position is less than zero, the returned characters counting will start from the first position.

If the value of the starting position is greater than the length of the specified string, the empty string is returned.

## Example

`MID ("Sample", 2, 3)` returns "amp".

## Additional resources

[Text functions](er-functions-category-text.md)
