---
# required metadata

title: CONVERTCURRENCY ER function
description: This topic provides information about how the CONVERTCURRENCY Electronic reporting (ER) function is used.
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

# <a name="CONVERTCURRENCY">CONVERTCURRENCY ER function</a>

[!include [banner](../includes/banner.md)]

The `CONVERTCURRENCY` function returns a *Real* value that represents the result of converting the specified monetary amount from the specified source currency to the specified target currency by using the settings of the specified company on the specified date.

## Syntax

```
CONVERTCURRENCY (amount, source currency, target currency, date, company)
```

## Arguments

`amount`: *Integer* or *Real*

A numeric value that represents the monetary amount that must be converted.

`source currency`: *String*

The code of the source currency.

`target currency`: *String*

The code of the target currency.

`date`: *Date*

A *Date* value that represents the date that is used to determine the exchange rate for the conversion.

`company`: *String*

A *String* value that represents the code of a company that supplies the settings that are used for the conversion.

## Return values

*Real*

The resulting numeric value.

## Example

`CONVERTCURRENCY (1, "EUR", "USD", TODAY(), "DEMF")` returns the equivalent of one euro in US dollars on the current session date, based on settings for the **DEMF** company.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
