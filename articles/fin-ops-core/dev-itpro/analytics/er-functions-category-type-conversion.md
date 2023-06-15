---
title: List of ER functions in the type conversion category
description: This article provides information about the conversion functions that are supported in Electronic reporting (ER).
author: kfend
ms.date: 12/05/2019
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

# List of ER functions in the type conversion category

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) type conversion functions can be used to convert values between types. This article provides a summary of these functions.

## Type conversion functions

| Function | Description |
|----------|-------------|
| [Int64Value](er-functions-conversion-int64value.md)   | This function returns an *Int64* value that represents the specified string. |
| [IntValue](er-functions-conversion-intvalue.md)       | This function returns an *Int* value that represents the specified string. |
| [NumberValue](er-functions-conversion-numbervalue.md) | This function returns a *Real* value that is converted from the specified *String* value. During the conversion, the specified decimal and digit grouping separators are considered. |
| [Value](er-functions-conversion-value.md)             | This function returns a *Real* value that is converted from the specified *String* value. |

## Type conversion functions in the container category

The following table describes the type conversion functions in the [container](er-functions-category-container.md) category.

| Function | Description |
|----------|-------------|
| [Base64StringToContainer](er-functions-container-base64stringtocontainer.md) | This function converts the specified input of the *String* type to a data item of the *Container* type. |

## Type conversion functions in the date and time category

The following table describes the type conversion functions in the [date and time category](er-functions-category-datetime.md).

| Function | Description |
|----------|-------------|
| [DateTimeValue](er-functions-datetime-datetimevalue.md)   | This function returns a *DateTime* value that is converted from a given *String* value in the specified format and in an optionally specified culture to a date/time value. |
| [DateToDateTime](er-functions-datetime-datetodatetime.md) | This function returns a *DateTime* value that is converted from a given *Date* value to a date/time value in Coordinated Universal Time (Greenwich Mean Time \[GMT\]). |
| [DateValue](er-functions-datetime-datevalue.md)           | This function returns a *Date* value that is converted from a given *String* value in the specified format and in an optionally specified culture to a date value. |

## Type conversion functions in the list category

The following table describes the type conversion functions in the [list category](er-functions-category-list.md).

| Function | Description |
|----------|-------------|
| [List](er-functions-list-list.md)                 | This function returns a *Record list* value as a new list that is created from specified arguments of the *Container (record)* type. |
| [ListOfFields](er-functions-list-listoffields.md) | This function returns a *Record list* value that is created based on the structure of a given argument of the *Enumeration* or *Container (record)* type. |
| [Split](er-functions-list-split.md)               | This function splits the specified *String* value into substrings and returns the result as a new *Record list* value. |
| [StringJoin](er-functions-list-stringjoin.md)     | This function returns a *String* value that consists of concatenated values of the specified field from the specified *Record list* value. The values can be separated by the specified delimiter. |

## Type conversion functions in the text category

The following table describes the type conversion functions in the [text category](er-functions-category-text.md).

| Function | Description |
|----------|-------------|
| [Char](er-functions-text-char.md)                 | This function returns a *String* value that represents a single character that is referenced by the specified Unicode number. |
| [GuidValue](er-functions-text-guidvalue.md)       | This function converts the specified input of the *String* type to a data item of the *GUID* type. |
| [NumberFormat](er-functions-text-numberformat.md) | This function returns a *String* value that represents the specified number in the specified format and in an optionally specified culture. |
| [QrCode](er-functions-text-qrcode.md)             | This function returns a *Container* value that presents the Quick Response code (QR code) image for the specified string in binary format. |
| [Text](er-functions-text-text.md)                 | This function returns a *String* value that represents the specified number after it has been converted to a text string that is formatted according to the server locale settings of the current application instance. |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
