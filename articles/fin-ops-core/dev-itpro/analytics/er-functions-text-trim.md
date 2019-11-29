---
# required metadata

title: TRIM ER function
description: This topic explains how the TRIM ER function is used
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

# <a name="TRIM">TRIM Function</a>

[!include [banner](../includes/banner.md)]

The `TRIM` function returns a *String* value of the specified text after leading and trailing spaces have been truncated, and after multiple spaces between words have been removed.

## Syntax

```
TRIM (text )
```

## Arguments

`text` : *String*

A valid path to a data source of the *String* type.

## Returns

*String*

The result text value.

## Example

`TRIM ("`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Sample`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`text`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`")` returns **"Sample text"**.

## Additional resources

[Text functions](er-functions-category-text.md)
