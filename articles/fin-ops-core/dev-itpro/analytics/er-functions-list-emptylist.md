---
# required metadata

title: EMPTYLIST ER function
description: This topic provides information about how the EMPTYLIST Electronic reporting (ER) function is used.
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

# EMPTYLIST ER function

[!include [banner](../includes/banner.md)]

The `EMPTYLIST` function returns an empty *Record list* value by using the specified list as a source for the list structure.

## Syntax

```vb
EMPTYLIST (list)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

## Return values

*Record list*

The resulting list of records.

## Example

`EMPTYLIST (SPLIT ("abc", 1))` returns a new empty list that has the same structure as the list that is returned by the `SPLIT` function that is used.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]