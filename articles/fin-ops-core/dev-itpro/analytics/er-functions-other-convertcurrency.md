---
title: CONVERTCURRENCY ER function
description: This article provides information about how the CONVERTCURRENCY Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/17/2019
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

# CONVERTCURRENCY ER function

[!include [banner](../includes/banner.md)]

The `CONVERTCURRENCY` function returns a *Real* value that represents the result of converting the specified monetary amount from the specified source currency to the specified target currency by using the settings of the specified company on the specified date.

## Syntax

```vb
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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
