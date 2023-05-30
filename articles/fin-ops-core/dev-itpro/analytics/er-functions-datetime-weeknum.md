---
title: WEEKNUM ER function
description: This article provides information about how the WEEKNUM Electronic reporting (ER) function is used.
author: kfend
ms.date: 01/15/2022
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2021-12-03
ms.dyn365.ops.version: AX 10.0.24
ms.assetid: 
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# WEEKNUM ER function

[!include [banner](../includes/banner.md)]

The `WEEKNUM` function returns an *[Integer](er-formula-supported-data-types-primitive.md#integer)* value that represents the week of the year that includes a specified *[Date](er-formula-supported-data-types-primitive.md#date)* value. The calculation is based on culture-dependent rules that define a calendar week and the first day of the week.

## Syntax

```vb
WEEKNUM (date, culture) as Integer
```

## <a name="arguments">Arguments</a>

`date`: *Date*

A date value that represents the date to use to calculate the week of the year.

`culture`: *[String](er-formula-supported-data-types-primitive.md#string)*

The culture to use for the calculation. You can use culture codes that are supported in accordance with .NET [standards](/dotnet/api/system.globalization.cultureinfo.getcultures?view=net-5.0).

## Return values

*Integer*

The resulting numeric value.

## Usage notes

The week of the year is calculated based on the [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) standard, if this standard has been adopted by a country or region that the locale is provided for at runtime. Otherwise, the calculation is based on country/region-specific national standards.

If an unsupported [culture](#arguments) code is provided as an argument of the `WEEKNUM` function at runtime, an exception is thrown. If the blank string is provided as a culture code, the English country-neutral calendar is used to calculate the week number.

## Examples

`WEEKNUM (DATEVALUE ("01-01-2020", "de"))` returns **1**.

`WEEKNUM (DATEVALUE ("01-01-2021", "de"))` returns **53**.

`WEEKNUM (DATEVALUE ("01-01-2022", "de"))` returns **52**.

`WEEKNUM (DATEVALUE ("01-01-2022", "ar"))` returns **21**.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
