---
title: List of ER functions of the text category
description: This article provides information about the text functions that are supported in Electronic reporting (ER).
author: kfend
ms.date: 02/28/2022
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

# List of ER functions of the text category

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) text functions can be used to perform operations on data sources of the *String* data type. This article provides a summary of these functions.

## List of supported functions

| Function | Description |
|----------|-------------|
| [Char](er-functions-text-char.md) | This function returns a *String* value that presents a single character that is referenced by the specified Unicode number. |
| [Concatenate](er-functions-text-concatenate.md) | This function returns all the specified text strings as a *String* value after they have been joined into one string. |
| [Format](er-functions-text-format.md) | This function returns the specified string a *String* value after it has been formatted by substituting any occurrences of **%N** with the *N*th argument. |
| [GetEnumValueByName](er-functions-text-getenumvaluebyname.md) | This function searches for a specific *Enum* value in the specified enumeration data source by using the enumeration name that is specified as a *String* value. If the *Enum* value is found, the function returns it. |
| [GetLabelText](er-functions-text-getlabeltext.md) | This function searches for a specific label to return a *[String](er-formula-supported-data-types-primitive.md#string)* value that represents the translation of the specified label in the specified language. |
| [GuidValue](er-functions-text-guidvalue.md) | This function converts the specified input of the *String* type to a data item of the *GUID* type. |
| [JsonValue](er-functions-text-jsonvalue.md) | This function parses data in JavaScript Object Notation (JSON) format that is accessed at the specified path, and it extracts a scalar value that is based on the specified ID. It then returns the extracted scalar value as a *String* value. |
| [Left](er-functions-text-left.md) | This function returns a *String* value that presents the specified number of characters from the start of the specified string. |
| [Len](er-functions-text-len.md) | This function returns an *Integer* value that presents the number of characters in the specified string. |
| [Lower](er-functions-text-lower.md) | This function returns the specified text string as a *String* value after it has been converted to lowercase letters. |
| [Mid](er-functions-text-mid.md) | This function returns a *[String](er-formula-supported-data-types-primitive.md#string)* value that presents the specified number of characters from the specified string, starting at the specified position. |
| [NewGUID](er-functions-text-newguid.md) | This function returns a newly generated *[GUID](er-formula-supported-data-types-primitive.md#guid)* value. |
| [NumberFormat](er-functions-text-numberformat.md) | This function returns a *String* value that presents the specified number in the specified format and in an optionally specified culture. |
| [NumeralsToText](er-functions-text-numeralstotext.md) | This function returns the specified number as a *String* value after it has been spelled out (that is, converted to text strings) in the specified language. |
| [PadLeft](er-functions-text-padleft.md) | This function returns a *String* value of the specified length, where the start of the specified string is padded with one or more instances of the specified characters. |
| [QrCode](er-functions-text-qrcode.md) | This function returns a *Container* value that presents the Quick Response code (QR code) image for the specified string in binary format. |
| [Replace](er-functions-text-replace.md) | This function returns the specified text string as a *String* value after all or part of it has been replaced with another string. |
| [Right](er-functions-text-right.md) | This function returns a *String* value that presents the specified number of characters from the end of the specified string. |
| [Text](er-functions-text-text.md) | This function returns the specified number as a *String* value after it has been converted to a text string that is formatted according to the server locale settings of the current application instance. |
| [Translate](er-functions-text-translate.md) | This function returns a *String* value that contains the result of the replacement the specified text in characters for another provided set of characters. |
| [Trim](er-functions-text-trim.md) | This function returns the specified text string as a *String* value after tab, carriage return, line feed, and form feed characters have been replaced by a single space character, after leading and trailing spaces have been truncated, and after multiple spaces between words have been removed. |
| [Upper](er-functions-text-upper.md) | This function returns the specified text string as a *String* value after it has been converted to uppercase letters. |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
