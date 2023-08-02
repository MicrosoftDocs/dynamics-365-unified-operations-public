---
title: TRIM ER function
description: This article provides information about how the TRIM Electronic reporting (ER) function is used.
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

# TRIM ER function

[!include [banner](../includes/banner.md)]

The `TRIM` function returns the specified text string as a *String* value after tab, carriage return, line feed, and form feed characters have been replaced by a single space character, after leading and trailing spaces have been truncated, and after multiple spaces between words have been removed.

## Syntax

```vb
TRIM (text)
```

## Arguments

`text`: *String*

The valid path of a data source of the *String* type.

## Return values

*String*

The resulting text value.

## Usage notes

In some cases, you might want to truncate leading and trailing spaces but prefer to keep formatting for the specified text. For example, when this text represents an address that could be entered in the multi-line text box and could contain line feed and carriage return formatting. In this case, use the following expression: `REPLACE(text,"^[ \t]+|[ \t]+$","", true)` where `text` is the argument that refers to the specified text string.

## Example 1

`TRIM ("`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Sample`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`text`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`")` returns **"Sample text"**.

## Example 2

`TRIM (CONCATENATE (CHAR(10), "`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Sample`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`", CHAR(9),"`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`text`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`", CHAR(13)))` returns **"Sample text"**.

## Additional resources

[Text functions](er-functions-category-text.md)

[REPLACE ER function](er-functions-text-replace.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
