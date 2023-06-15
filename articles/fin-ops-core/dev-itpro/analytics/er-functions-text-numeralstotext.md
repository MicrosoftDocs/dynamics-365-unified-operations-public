---
title: NUMERALSTOTEXT ER function
description: This article provides information about how the NUMERALSTOTEXT Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/10/2019
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

# NUMERALSTOTEXT ER function

[!include [banner](../includes/banner.md)]

The `NUMERALSTOTEXT` function returns the specified number as a *String* value after it has been spelled out (that is, converted to text strings) in the specified language.

## Syntax

```vb
NUMERALSTOTEXT (number, language, currency, print currency name flag, decimal points)
```

## Arguments

`number`: *Integer* or *Real*

A numeric value that specifies the number that must be spelled out.

`language`: *String*

A *String* value that represents the language code.

`currency`: *String*

A *String* value that represents the currency code.

`print currency name flag`: *Boolean*

A *Boolean* value that indicates whether a currency name must be added to the spelled-out text.

`decimal points`: *Integer*

An *Integer* value that indicates the number of decimal places that the spelled-out text should have.

## Return values

*String*

The resulting text value.

## Usage notes

The language code is optional. If it's defined as an empty string, the language code for the running context is used. The default language code is **EN-US**. The language code for the running context is defined in a **Folder** or **File** element of the Electronic reporting (ER) format that is running.

The currency code is optional. If it's defined as an empty string, the company currency for the running context is used.

> [!NOTE] 
> The `print currency name flag` and `decimal points` arguments are analyzed only for the following language codes: **CS**, **ET**, **HU**, **LT**, **LV**, **PL**, and **RU**. Additionally, the `print currency name flag` argument is analyzed only for companies where the country's or region's context supports declension of currency names.

## Example 1

`NUMERALSTOTEXT (1234.56, "EN-US", "", false, 2)` returns **"One Thousand Two Hundred Thirty Four and 56"**.

## Example 2

`NUMERALSTOTEXT (120, "PL", "", false, 0)` returns **"Sto dwadzieścia"**. 

## Example 3

`NUMERALSTOTEXT (120.21, "RU", "EUR", true, 2)` returns **"Сто двадцать евро 21 евроцент"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
