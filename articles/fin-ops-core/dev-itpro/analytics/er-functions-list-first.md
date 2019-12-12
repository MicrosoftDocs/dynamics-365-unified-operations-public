---
# required metadata

title: FIRST ER function
description: This topic provides information about how the FIRST ER function is used.
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

# <a name="FIRST">FIRST Function</a>

[!include [banner](../includes/banner.md)]

The `FIRST` function returns the first record of the specified list as a *Container (record)*, if that list is not empty. Otherwise, throws an exception.

## Syntax

```
FIRST (list)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

## Returns

*Container (record)*

The result record value.

## Example 1

The `FIRST(SPLIT("ABC",1)).Value` expression returns the text value, “A”.

## Example 2

The `FIRST(SPLIT("",1)).Value` expression throws an exception at runtime.

## Additional resources

[List functions](er-functions-category-list.md)
