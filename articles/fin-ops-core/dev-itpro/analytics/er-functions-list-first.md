---
# required metadata

title: FIRST ER function
description: This topic provides information about how the FIRST Electronic reporting (ER) function is used.
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

# FIRST ER function

[!include [banner](../includes/banner.md)]

The `FIRST` function returns the first record of the specified list as a *Container (record)* value, if that list isn't empty. If the list is empty, this function throws an exception.

## Syntax

```vb
FIRST (list)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

## Return values

*Container (record)*

The resulting record value.

## Example 1

The expression `FIRST(SPLIT("ABC",1)).Value` returns the text value **"A"**.

## Example 2

The expression `FIRST(SPLIT("",1)).Value` throws an exception at runtime.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]