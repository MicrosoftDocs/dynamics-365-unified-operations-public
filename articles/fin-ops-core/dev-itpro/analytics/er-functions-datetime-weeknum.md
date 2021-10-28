---
# required metadata

title: WEEKNUM ER function
description: This topic provides information about how the WEEKNUM Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 10/27/2021
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-10-27
ms.dyn365.ops.version: AX 10.0.24

---

# WEEKNUM ER function

[!include [banner](../includes/banner.md)]

The `WEEKNUM` function returns an *[Integer](er-formula-supported-data-types-primitive.md#integer)* value that represents the week of the year that includes the specified *[Date](er-formula-supported-data-types-primitive.md#date)* value based on culture dependent rules of defining a calendar week and the first day of the week.

## Syntax

```vb
WEEKNUM (date, culture) as Integer
```

## <a name="arguments">Arguments</a>

`date`: *Date*

A date value that represents the date to use for the calculation of the week of the year.

`culture`: *[String](er-formula-supported-data-types-primitive.md#string)*

The culture to use for calculation. You can use culture codes that are supported in accordance with .NET [standards](https://docs.microsoft.com/dotnet/api/system.globalization.cultureinfo.getcultures?view=net-5.0).

## Return values

*Integer*

The resulting numeric value.

## Usage notes

The week of the year is calculated based on the [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) standard when this standard has been adopted by a country the locale of which is provided at runtime. Otherwise, this calculation is performed based on country specific national standards.

When a non-supported [culture](#arguments) code is provided at runtime as an argument of the WEEKNUM function, an exception is thrown. When the blank string is provided as a culture code, the English country neutral calendar is used for week number calculation.

## Examples

`WEEKNUM (DATEVALUE ("01-01-2020", "de"))` returns 1.

`WEEKNUM (DATEVALUE ("01-01-2021", "de"))` returns 53.

`WEEKNUM (DATEVALUE ("01-01-2022", "de"))` returns 52.

`WEEKNUM (DATEVALUE ("01-01-2022", "ar"))` returns 21.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
