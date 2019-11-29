---
# required metadata

title: EMPTYLIST ER function
description: This topic explains how the EMPTYLIST ER function is used
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

# <a name="EMPTYLIST">EMPTYLIST Function</a>

[!include [banner](../includes/banner.md)]

The `EMPTYLIST` function returns an empty *Record list* by using the specified list as a source for the list structure.

## Syntax

```
EMPTYLIST (list)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

## Returns

*Record list*

The result list of records.

## Example

`EMPTYLIST (SPLIT ("abc", 1))` returns a new empty list that has the same structure as the list that is returned in this example by the `SPLIT` function.


## Additional resources

[List functions](er-functions-category-list.md)
