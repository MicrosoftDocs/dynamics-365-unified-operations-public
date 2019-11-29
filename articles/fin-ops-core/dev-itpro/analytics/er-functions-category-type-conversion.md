---
# required metadata

title: List of ER functions of the type conversion category
description: This topic explains what type conversion functions are supported in ER
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

# Type conversion functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) type conversion functions can be used to convert values between types. The following is a summary of conversion functions in ER.

## List of type conversion functions

| **Function**                | **Description**               |
|-----------------------------|-------------------------------|
| [Int64Value](er-functions-conversion-int64value.md)         | Returns an *Int64* representation of the specified string.   |
| [IntValue](er-functions-conversion-intvalue.md)             | Returns an *Int* representation of the specified string.     |
| [NumberValue](er-functions-conversion-numbervalue.md)       | Returns a *Real* value that is converted from the specified *String* value considering the specified decimal and digit grouping separators.                                          |
| [Value](er-functions-conversion-value.md)                   | Returns a *Real* value that is converted from the specified *String* value.                                               |

## List of type conversion functions of the [Date & Time category](er-functions-category-datetime.md)

| **Function**                | **Description**               |
|-----------------------------|-------------------------------|
| [DateTimeValue](er-functions-datetime-datetimevalue.md)     | Returns a *DateTime* value that is converted from a given *String* value in the specified format and an optionally specified culture to a datetime value.                        |
| [DateToDateTime](er-functions-datetime-datetodatetime.md)   | Returns a *DateTime* value that is converted from a given *Date* value to a datetime value in the GMT time zone.        |
| [DateValue](er-functions-datetime-datevalue.md)             | Returns a *Date* value that is converted from a given *String* value in the specified format and an optionally specified culture to a date value.                            |

## List of type conversion functions of the [List](er-functions-category-list.md) category

| **Function**                | **Description**               |
|-----------------------------|-------------------------------|
| [List](er-functions-list-list.md)                           | Returns a *Record list* as a new list that is created from specified arguments of the *Container (record)* type.         |
| [ListOfFields](er-functions-list-listoffields.md)           | Returns a *Record list* that is created based on the structure of a given argument of one of the following types: *Enumeration* or *Container (record)*.                        |
| [Split](er-functions-list-split.md)                         | Splits the specified *String* value into substrings. Returns the result as a new *Record list*.                            |
| [StringJoin](er-functions-list-stringjoin.md)               | Returns a *String* that consists of concatenated values of the specified field from the specified *Record list*. The values can be separated by the specified delimiter.           |

## List of type conversion functions of the [Text](er-functions-category-text.md) category

| **Function**                | **Description**               |
|-----------------------------|-------------------------------|
| [Char](er-functions-text-char.md)                           | Returns a *String* value as the set of characters that is referenced by the specified Unicode number.                   |
| [GuidValue](er-functions-text-guidvalue.md)                 | Converts the specified input of the *String* type to a data item of the *GUID* type.                                      |
| [NumberFormat](er-functions-text-numberformat.md)           | Returns a *String* representation of the specified number in the specified format and an optionally specified culture.     |
| [QrCode](er-functions-text-qrcode.md)                       | Returns a *Container* value of the Quick Response Code (QR code) image in binary format for the specified string.        |
| [Text](er-functions-text-text.md)                           | Returns a *String* value of the specified number after it has been converted to a text string that is formatted according to the server locale settings of the current application instance.                                                     |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)
