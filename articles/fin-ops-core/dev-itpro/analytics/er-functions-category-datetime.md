---
# required metadata

title: List of ER functions of the Date and time category
description: This topic explains what Date and time functions are supported in ER
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

# Date and time functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) date and time functions can be used to extract information from, and perform operations on, dates and times values. You can find a summary of such functions below in this article.

## List of supported functions

| **Function** | **Description** |
|--------------|-----------------|
| [AddDays](er-functions-datetime-adddays.md)               | Returns a *DateTime* value before or after the specified number of days.                                             |
| [DateFormat](er-functions-datetime-dateformat.md)         | Returns a *String* value presenting a given date value as a text in the specified format and an optionally specified culture.                                                    |
| [DateTimeFormat](er-functions-datetime-datetimeformat.md) | Returns a *String* value presenting a given datetime value as a text in the specified format and an optionally specified culture.                                                    |
| [DateTimeValue](er-functions-datetime-datetimevalue.md)   | Returns a *DateTime* value that is converted from a given text value in the specified format and an optionally specified culture to a datetime value.                                |
| [DateToDateTime](er-functions-datetime-datetodatetime.md) | Returns a *DateTime* value that is converted from a given date value to a datetime value in the GMT time zone.             |
| [DateValue](er-functions-datetime-datevalue.md)           | Returns a *Date* value that is converted from a given text value in the specified format and an optionally specified culture to a date value.                                    |
| [DayOfYear](er-functions-datetime-dayofyear.md)           | Returns an *Integer* value that represents the the number of days between January 1 and the specified date.              |
| [Days](er-functions-datetime-days.md)                     | Returns an *Integer* value that represents the number of days between the first specified date and the second specified date.                                                       |
| [Now](er-functions-datetime-now.md)                       | Returns a *DateTime* value of the current application server date and time.                                              |
| [NullDate](er-functions-datetime-nulldate.md)             | Returns a *Date* value of the **null** date value (Jan 1st, 1900).                                                      |
| [NullDateTime](er-functions-datetime-nulldatetime.md)     | Returns a *DateTime* value of the **null** datetime value (Jan 1st, 1900) in the GMT time zone.                            |
| [SessionNow](er-functions-datetime-sessionnow.md)         | Returns a *DateTime* value of the current application session date and time.                                              |
| [SessionToday](er-functions-datetime-sessiontoday.md)     | Returns a *Date* value of the current application session date.                                                       |
| [Today](er-functions-datetime-today.md)                   | Returns a *Date* value of the current application server date.                                                             |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)
