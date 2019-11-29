---
# required metadata

title: INDEX ER function
description: This topic explains how the INDEX ER function is used
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

# <a name="INDEX">INDEX Function</a>

[!include [banner](../includes/banner.md)]

The `INDEX` function returns a *Container (record)* that is selected by a specific numeric index in the specified list. An exception is thrown if the index is out of range of the records in the specified list.

## Syntax

```
INDEX (list, index)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

`index` : *Integer*

A numeric index indicating the position of a desired record in a given list.

## Returns

*Container (record)*

The result record value.

## Example 1

If you enter the data source **DS** of the *Calculated field* type and it contains the expression `SPLIT ("A|B|C", “|”)`, the expression `DS.Value` returns the text value, “B” for the 2nd record of this record list. The expression `INDEX (SPLIT ("A|B|C", “|”), 2).Value` also returns the “B” text value.

## Example 2

If you enter the data source **DS** of the *Calculated field* type and it contains the expression `SPLIT ("A|B|C", “|”)`, the expression `INDEX (SPLIT ("A|B|C", “|”), 4).Value` throws an exception at runtime.

## Additional resources

[List functions](er-functions-category-list.md)
