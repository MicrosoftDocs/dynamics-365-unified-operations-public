---
title: List of ER functions in the Date and time category
description: This article provides information about the date and time functions that are supported in Electronic reporting (ER).
author: kfend
ms.date: 09/09/2021
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

# List of ER functions in the Date and time category

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) date and time functions can be used to extract information from date and time values, and to perform operations on them. This article provides a summary of these functions.

## List of supported functions

| Function | Description |
|----------|-------------|
| [AddDays](er-functions-datetime-adddays.md) | This function returns a *[DateTime](er-formula-supported-data-types-primitive.md#datetime)* value that is the specified number of days before or after a specified start date. |
| [ChangeTimeZone](er-functions-datetime-changetimezone.md) | This function returns a *DateTime* value that is converted from a given date/time value in one time zone to a date/time value in another time zone. |
| [DateFormat](er-functions-datetime-dateformat.md) | This function returns a *[String](er-formula-supported-data-types-primitive.md#string)* value that presents a given date value as text in the specified format and in an optionally specified culture. |
| [DateTimeFormat](er-functions-datetime-datetimeformat.md) | This function returns a *String* value that presents a given date/time value as text in the specified format and in an optionally specified culture. |
| [DateTimeValue](er-functions-datetime-datetimevalue.md) | This function returns a *DateTime* value that is converted from a given text value in the specified format and in an optionally specified culture to a date/time value. |
| [DateToDateTime](er-functions-datetime-datetodatetime.md) | This function returns a *DateTime* value that is converted from a given date value to a date/time value in Coordinated Universal Time (Greenwich Mean Time \[GMT\]). |
| [DateValue](er-functions-datetime-datevalue.md) | This function returns a *[Date](er-formula-supported-data-types-primitive.md#date)* value that is converted from a given text value in the specified format and in an optionally specified culture to a date value. |
| [DayOfYear](er-functions-datetime-dayofyear.md) | This function returns an *[Integer](er-formula-supported-data-types-primitive.md#integer)* value that represents the number of days between January 1 and the specified date. |
| [Days](er-functions-datetime-days.md) | This function returns an *Integer* value that represents the number of days between one specified date and a second specified date. |
| [Now](er-functions-datetime-now.md) | This function returns a *DateTime* value that represents the current application server date and time. |
| [NullDate](er-functions-datetime-nulldate.md) | This function returns a *Date* value that represents the **null** date (January 1, 1900). |
| [NullDateTime](er-functions-datetime-nulldatetime.md) | This function returns a *DateTime* value that represents the **null** date/time value (January 1, 1900) in Coordinated Universal Time. |
| [SessionNow](er-functions-datetime-sessionnow.md) | This function returns a *DateTime* value that represents the current application session date and time. |
| [SessionToday](er-functions-datetime-sessiontoday.md) | This function returns a *Date* value that represents the current application session date. |
| [Today](er-functions-datetime-today.md) | This function returns a *Date* value that represents the current application server date. |
| [WeekNum](er-functions-datetime-weeknum.md) | This function returns an *Integer* value that represents the week of the year. |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
