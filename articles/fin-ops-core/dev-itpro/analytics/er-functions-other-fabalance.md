---
# required metadata

title: FA_BALANCE ER function
description: This topic provides information about how the FA_BALANCE ER function is used.
author: NickSelin
manager: kfend
ms.date: 12/17/2019
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

# <a name="FA_BALANCE">FA_BALANCE Function</a>

[!include [banner](../includes/banner.md)]

The `FA_BALANCE` function returns a *Container (record)* of data of the fixed asset balance for the specified fixed asset item, value model code, reporting year, and reporting date.

## Syntax

```
FA_BALANCE (fixed asset code, value model code, reporting year, reporting date)
```

## Arguments

`fixed asset code` : String

A *String* value representing the code of a fixed asset item for which the balance is calculated.

`value model code` : String

A *String* value representing the code of a value model for which the balance is calculated.

`reporting year` : *Enumeration value*

An enumeration value of the **AssetYear** application enumeration defining a period for balance calculation.

`reporting date` : *Date*

A *Date* value defining a date for balance calculation.

## Returns

*Container (record)*

The result record value.

## Example

`FA_ BALANCE ("COMP-000001", "Current", AxEnumAssetYear.ThisYear, SESSIONTODAY ())` returns the prepared data container of balances for fixed asset "COMP-000001" that has been prepared for the "Current" value model on the current application session date.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
