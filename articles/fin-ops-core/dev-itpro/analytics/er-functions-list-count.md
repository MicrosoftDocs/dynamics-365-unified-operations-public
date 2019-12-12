---
# required metadata

title: COUNT ER function
description: This topic provides information about how the COUNT ER function is used.
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

# <a name="COUNT">COUNT Function</a>

[!include [banner](../includes/banner.md)]

The `COUNT` function returns an *Integer* value as the number of records in the specified list, if the list is not empty. Otherwise, it returns zero (0).

## Syntax

```
COUNT (list)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

## Returns

*Integer*

The result numeric value.

## Example

`COUNT (SPLIT("abcd" , 3))` returns **2**, because the `SPLIT` function creates in this example a list that consists of two records.

## Additional resources

[List functions](er-functions-category-list.md)
