---
# required metadata

title: CONVERTCURRENCY ER function
description: This topic provides information about how the CONVERTCURRENCY ER function is used.
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

# <a name="CONVERTCURRENCY">CONVERTCURRENCY Function</a>

[!include [banner](../includes/banner.md)]

The `CONVERTCURRENCY` function returns a *Real* value as the result of the conversion of the specified monetary amount from the specified source currency to the specified target currency by using the settings of the specified company on the specified date.

## Syntax

```
CONVERTCURRENCY (amount, source currency, target currency, date, company)
```

## Arguments

`amount` : *Integer* or *Real*

A numeric value of the monetary amount that must be converted.

`source currency` : *String*

A code of the source currency.

`target currency` : *String*

A code of the target currency.

`date` : *Date*

A Date value of date using to specify the exchange rate for conversion.

`company` : *String*

A String value of the code of a company the settings of which are used for conversion.

## Returns

*Real*

The result numeric value.

## Example

`CONVERTCURRENCY (1, "EUR", "USD", TODAY(), "DEMF")` returns the equivalent of one euro in US dollars on the current session date, based on settings for the **DEMF** company.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
