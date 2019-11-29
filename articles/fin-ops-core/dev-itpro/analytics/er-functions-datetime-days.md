---
# required metadata

title: DAYS ER function
description: This topic explains how the DAYS ER function is used
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

# <a name="DAYS">DAYS Function</a>

[!include [banner](../includes/banner.md)]

The `DAYS` function returns an *Integer* value that represents the number of days between the first specified date and the second specified date.

## Syntax

```
DAYS (date 1, date 2) as Integer
```

## Arguments

`date 1` : *Date*

A date that represents the start date for calculation of number of days.

`date 2` : *Date*

A date that represents the end date for calculation of number of days.

## Returns

*Integer*

The result numeric value.

## Usage notes

The `DAYS` function returns a positive value when the first date is later than the second date, returns **0** (zero) when the first date equals the second date, or returns a negative value when the first date is earlier than the second date.

## Example

`DAYS (TODAY (), DATEVALUE( DATETIMEFORMAT( ADDDAYS ( NOW(), 1), "yyyyMMdd"),
"yyyyMMdd"))` returns **-1**.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)
