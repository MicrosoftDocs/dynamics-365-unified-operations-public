---
title: DATETIMEFORMAT ER function
description: This article provides information about how the DATETIMEFORMAT Electronic reporting (ER) function is used.
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

# DATETIMEFORMAT ER function

[!include [banner](../includes/banner.md)]

The `DATETIMEFORMAT` function returns a *[String](er-formula-supported-data-types-primitive.md#string)* value that presents a given date/time value as text in the specified format and in an optionally specified [culture](/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes). For information about the supported formats, see [standard](/dotnet/standard/base-types/standard-date-and-time-format-strings) and [custom](/dotnet/standard/base-types/custom-date-and-time-format-strings).

## Syntax 1

```vb
DATETIMEFORMAT (datetime, format)
```

## Syntax 2

```vb
DATETIMEFORMAT (datetime, format, culture)
```

## Arguments

`datetime`: *[DateTime](er-formula-supported-data-types-primitive.md#datetime)*

A date/time value that represents the date and time to format.

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

If the culture isn't defined as an argument of the called function, the value of `culture` is defined by the calling context. For example, if the `DATETIMEFORMAT` function is called by using syntax 1 in an Electronic reporting (ER) format for a **FILE** element that is configured to use the German culture, the conversion will be done by using the German culture. The default `culture` value is **EN-US**.

When the `DATETIMEFORMAT` function converts a given date/time value, it considers the time zone setting of the application user who is running the ER format that the function is called in the context of.

## Example 1

`DATETIMEFORMAT (NOW(), "dd-MM-yyyy")` returns the current application server date/time value, December 24, 2015, as **"24-12-2015"**, based on the specified custom format.

## Example 2

`DATETIMEFORMAT (SESSIONNOW(), "d", "DE")` returns the current application session date/time value, December 24, 2015, as **"24.12.2015"**, based on the selected German culture and the specified format.

## Example 3

`DATETIMEFORMAT (DATETIMEVALUE( "2019-11-12T09:00:00.0000000-07:00", "O"), "O")` returns the string value **2019-11-12T08:00:00.0000000-08:00** when the function is called during a process that was initiated by an application user who has the time zone value **(GMT-08:00) Pacific Time (US & Canada)** in the **Language and country/region preferences** section.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
