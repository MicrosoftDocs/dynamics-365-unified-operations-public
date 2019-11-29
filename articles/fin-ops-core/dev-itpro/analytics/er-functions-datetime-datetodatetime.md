---
# required metadata

title: DATETODATETIME ER function
description: This topic explains how the DATETODATETIME ER function is used
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

# <a name="DATETODATETIME">DATETODATETIME Function</a>

[!include [banner](../includes/banner.md)]

The `DATETODATETIME` function returns a *DateTime* value that is converted from a given date value to a datetime value in the GMT time zone.

## Syntax

```
DATETODATETIME (date)
```

## Arguments

`date` : *Date*

A date that represents the date for conversion.

## Returns

*DateTime*

The result datetime value.

## Example 1

`DATETODATETIME (CompInfo. 'getCurrentDate()')` returns the current Finance session date, December 24, 2015, as **12/24/2015 12:00:00 AM**. In this example, **CompInfo** is an ER data source of the **Finance and Operations/Table** type and refers to the **CompanyInfo** table.

## Example 2

`DATETODATETIME (DATEVALUE ("2019-11-12T16:00:00.0000000-07:00",
"O"))` returns the **11/12/2019 12:00:00 AM** datetime.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)
