---
title: DATEFORMAT ER function
description: This article provides information about how the DATEFORMAT Electronic reporting (ER) function is used.
author: kfend
ms.date: 09/08/2021
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

# DATEFORMAT ER function

[!include [banner](../includes/banner.md)]

The `DATEFORMAT` function returns a *[String](er-formula-supported-data-types-primitive.md#string)* value that presents a given date value as text in the specified format and in an optionally specified [culture](/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes). For information about the supported formats, see [standard](/dotnet/standard/base-types/standard-date-and-time-format-strings) and [custom](/dotnet/standard/base-types/custom-date-and-time-format-strings).

## Syntax 1

```vb
DATEFORMAT (date, format)
```

## Syntax 2

```vb
DATEFORMAT (date, format, culture)
```

## Arguments

`date`: *[Date](er-formula-supported-data-types-primitive.md#date)*

A date value that represents the date to format.

`format`: *String*

The format of the output string. For information about the supported formats, see [standard](/dotnet/standard/base-types/standard-date-and-time-format-strings) and [custom](/dotnet/standard/base-types/custom-date-and-time-format-strings).

> [!NOTE]
> The format string is case-sensitive when you use either a standard format or a custom format. For example, the [standard](/dotnet/standard/base-types/standard-date-and-time-format-strings) "d" format specifier returns the date by using the short date pattern, whereas the standard "D" format specifier returns the date by using the long date pattern. Additionally, the [custom](/dotnet/standard/base-types/custom-date-and-time-format-strings) "M" format specifier returns the month from 1 through 12, whereas the custom "m" format specifier returns the minute from 0 through 59.

`culture`: *String*

The culture to use for formatting. For information about the supported cultures, see [culture](/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes).

## Return values

*String*

The resulting string value.

## Usage notes

If the culture isn't defined as an argument of the called function, the value of `culture` is defined by the calling context. For example, if the `DATEFORMAT` function is called by using syntax 1 in an Electronic reporting (ER) format for a **FILE** element that is configured to use the German culture, the conversion will be done by using the German culture. The default `culture` value is **EN-US**.

## Example 1

`DATEFORMAT (TODAY (), "dd-MM-yyyy")` returns the current application server date, December 24, 2015, as the string **"24-12-2015"**, based on the specified custom format.

## Example 2

`DATEFORMAT (SESSIONTODAY (), "d", "DE")` returns the current application session date, December 24, 2015, as the string **"24-12-2015"**, based on the selected German culture and the specified format.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
