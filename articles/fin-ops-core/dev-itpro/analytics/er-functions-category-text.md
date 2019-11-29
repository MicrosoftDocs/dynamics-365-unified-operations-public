---
# required metadata

title: List of ER functions of the text category
description: This topic explains what text functions are supported in ER
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

# Text functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) text functions can be used to perform operations on data sources of the *String* data type. You can find a summary of such functions below in this article.

## List of supported functions

| **Function**    | **Description**   |
|-----------------|-------------------|
| [Char](er-functions-text-char.md)                           | Returns a *String* value as the set of characters that is referenced by the specified Unicode number.                   |
| [Concatenate](er-functions-text-concatenate.md)             | Returns a *String* value that presents all specified text strings after they have been joined into one string.          |
| [Format](er-functions-text-format.md)                       | Returns a *String* value of the specified string after it has been formatted by substituting any occurrences of **%N** with the **Nth** argument.                                         |
| [GetEnumValueByName](er-functions-text-getenumvaluebyname.md)| Searches for a specific *Enum* value in the specified enumeration data source by using the specified as *String* text enumeration name. Returns an *Enum* value when such value has been found.   |
| [GuidValue](er-functions-text-guidvalue.md)                   | Converts the specified input of the *String* type to a data item of the *GUID* type.                                                |
| [JsonValue](er-functions-text-jsonvalue.md)                   | Returns a *String* value as the result of parsing data in JavaScript Object Notation (JSON) format that is accessed by the specified path to extract a scalar value that is based on the specified ID. |
| [Left](er-functions-text-left.md)                             | Returns a *String* value as the specified number of characters from the start of the specified string.                              |
| [Len](er-functions-text-len.md)                               | Returns an *Integer* value of the number of characters in the specified string.                                               |
| [Lower](er-functions-text-lower.md)                           | Returns the specified string as a *String* value after it has been converted to lowercase letters.                                 |
| [Mid](er-functions-text-mid.md)                               | Returns a *String* value of the specified number of characters from the specified string, starting at the specified position.       |
| [NumberFormat](er-functions-text-numberformat.md)             | Returns a *String* representation of the specified number in the specified format and an optionally specified culture.           |
| [NumeralsToText](er-functions-text-numeralstotext.md)         | Returns a *String* representation of the specified number after it has been spelled out (converted to text strings) in the specified language.                                                       |
| [PadLeft](er-functions-text-padleft.md)                       | Returns a *String* of the specified length, where the start of the specified string is padded with the specified characters.                                                                           |
| [QrCode](er-functions-text-qrcode.md)                         | Returns a *Container* value of the Quick Response Code (QR code) image in binary format for the specified string.                |
| [Replace](er-functions-text-replace.md)                       | Returns a *String* value of the specified text replacing all or part of this text string with another string.                   |
| [Right](er-functions-text-right.md)                           | Returns a *String* value as the specified number of characters from the end of the specified string.                                |
| [Text](er-functions-text-text.md)                             | Returns a *String* value of the specified number after it has been converted to a text string that is formatted according to the server locale settings of the current application instance.     |
| [Translate](er-functions-text-translate.md)                   | Returns a *String* value of the specified text replacing all or part of this text string with another string.                   |
| [Trim](er-functions-text-trim.md)                             | Returns a *String* value of the specified text after leading and trailing spaces have been truncated, and after multiple spaces between words have been removed.                                |
| [Upper](er-functions-text-upper.md)                           | Returns the specified string as a *String* value after it has been converted to uppercase letters.                                 |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)
