---
# required metadata

title: CONCATENATE ER function
description: This topic provides information about how the CONCATENATE ER function is used
author: NickSelin
manager: kfend
ms.date: 12/12/2019
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

# <a name="CONCATENATE">CONCATENATE Function</a>

[!include [banner](../includes/banner.md)]

The `CONCATENATE` function returns a *String* value that presents all specified text strings after they have been joined into one string.

## Syntax

```
CONCATENATE (text 1 [, text 2, … , text N])
```

## Arguments

`text 1` : *String*

A reference to a data source of the *String* data type. One argument is mandatory.

`text N` : *String*

A reference to a data source of the *String* data type. Other arguments are optional.

## Returns

*String*

The result text value.

## Example

`CONCATENATE ("abc", "def")` returns "abcdef".

## Usage notes

> [!NOTE] 
> The expression `"abc" & "def"` also returns "abcdef".

## Additional resources

[Text functions](er-functions-category-text.md)
