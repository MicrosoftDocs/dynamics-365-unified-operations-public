---
# required metadata

title: DAYOFYEAR ER function
description: This topic provides information about how the DAYOFYEAR Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 12/04/2019
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

# DAYOFYEAR ER function

[!include [banner](../includes/banner.md)]

The `DAYOFYEAR` function returns an *Integer* value that represents the number of days between January 1 and the specified date.

## Syntax

```vb
DAYOFYEAR (date) as Integer
```

## Arguments

`date`: *Date*

A date value that represents the date to use for the calculation of the number of days.

## Return values

*Integer*

The resulting numeric value.

## Example 1

`DAYOFYEAR (DATEVALUE ("01-03-2016", "dd-MM-yyyy"))` returns **61**.

## Example 2

`DAYOFYEAR (DATEVALUE ("01-01-2016", "dd-MM-yyyy"))` returns **1**.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]