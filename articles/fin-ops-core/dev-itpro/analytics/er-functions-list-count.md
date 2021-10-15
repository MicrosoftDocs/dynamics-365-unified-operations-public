---
# required metadata

title: COUNT ER function
description: This topic provides information about how the COUNT Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 12/12/2019
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# COUNT ER function

[!include [banner](../includes/banner.md)]

The `COUNT` function returns an *Integer* value that represents the number of records in the specified list, if the list isn't empty. If the list is empty, this function returns **0** (zero).

## Syntax

```vb
COUNT (list)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

## Return values

*Integer*

The resulting numeric value.

## Example

`COUNT (SPLIT("abcd" , 3))` returns **2**, because the `SPLIT` function that is used in this example creates a list that consists of two records.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]