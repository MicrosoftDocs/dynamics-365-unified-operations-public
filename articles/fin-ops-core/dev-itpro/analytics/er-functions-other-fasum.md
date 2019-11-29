---
# required metadata

title: FA_SUM ER function
description: This topic explains how the FA_SUM ER function is used
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

# <a name="FA_SUM">FA_SUM Function</a>

[!include [banner](../includes/banner.md)]

The `FA_SUM` function returns a *Container (record)* of data of the fixed asset amounts for the specified fixed asset item, value model code, and period of dates.

## Syntax

```
FA_SUM (fixed asset code, value model code, start date, end date)
```

## Arguments

`fixed asset code` : *String*

A *String* value representing the code of a fixed asset item for which the balance is calculated.

`value model code` : String

A *String* value representing the code of a value model for which the balance is calculated.

`start date` : Date

A *Date* value representing the start date of a period for which the fixed asset amounts are calculated.

`end date` : *Date*

A *Date* value representing the end date of a period for which the fixed asset amounts are calculated.

## Returns

*Container (record)*

The result record value.

## Example

`FA_SUM ("COMP-000001", "Current", Date1, Date2)` returns the data container of the fixed asset "COMP-000001" that has been prepared for the "Current" value model and for a period from Date1 to Date2.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
