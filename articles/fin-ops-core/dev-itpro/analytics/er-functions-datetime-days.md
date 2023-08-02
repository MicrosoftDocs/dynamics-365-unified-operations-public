---
title: DAYS ER function
description: This article provides information about how the DAYS Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/04/2019
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# DAYS ER function

[!include [banner](../includes/banner.md)]

The `DAYS` function returns an *Integer* value that represents the number of days between one specified date and a second specified date.

## Syntax

```vb
DAYS (date 1, date 2) as Integer
```

## Arguments

`date 1`: *Date*

A date value that represents the start date for the calculation of the number of days.

`date 2`: *Date*

A date value that represents the end date for the calculation of the number of days.

## Return values

*Integer*

The resulting numeric value.

## Usage notes

The `DAYS` function returns a positive value when the first date is later than the second date, it returns **0** (zero) when the first date equals the second date, and it returns a negative value when the first date is earlier than the second date.

## Example

`DAYS (TODAY (), DATEVALUE( DATETIMEFORMAT( ADDDAYS ( NOW(), 1), "yyyyMMdd"), "yyyyMMdd"))` returns **-1**.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
