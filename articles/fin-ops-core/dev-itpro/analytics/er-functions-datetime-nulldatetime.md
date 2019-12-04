---
# required metadata

title: NULLDATETIME ER function
description: This topic provides information about how the NULLDATETIME ER function is used.
author: NickSelin
manager: kfend
ms.date: 12/04/2019
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

# <a name="NULLDATETIME">NULLDATETIME Function</a>

[!include [banner](../includes/banner.md)]

The `NULLDATETIME` function returns a *DateTime* value of the **null** datetime (Jan 1st, 1900) in the GMT time zone.

## Syntax

```
NULLDATETIME ()
```

## Returns

*DateTime*

The result datetime value.

## Example

`DATETIMEFORMAT( NULLDATETIME(), "O")` returns the
**1900-01-01T00:00:00.0000000+00:00** string value when this function is called in the process that has been initiated by an application user having the **(GMT) Coordinated Universal Time** time zone value in the **Language and country/region preferences** section.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)
