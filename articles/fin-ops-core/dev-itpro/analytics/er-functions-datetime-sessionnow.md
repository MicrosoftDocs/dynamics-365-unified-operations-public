---
# required metadata

title: SESSIONNOW ER function
description: This topic provides information about how the SESSIONNOW Electronic reporting (ER) function is used.
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

# SESSIONNOW ER function

[!include [banner](../includes/banner.md)]

The `SESSIONNOW` function returns a *DateTime* value that represents the current application session date and time.

## Syntax

```vb
SESSIONNOW ()
```

## Return values

*DateTime*

The resulting date/time value.

## Example

`DATETIMEFORMAT (SESSIONNOW(), "d", "DE")` returns the current application session date/time value, December 24, 2015, as **"24.12.2015"**, based on the selected German culture and the specified format.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]