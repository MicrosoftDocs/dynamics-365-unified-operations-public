---
# required metadata

title: NUMERALSTOTEXT ER function
description: This topic provides information about how the NUMERALSTOTEXT ER function is used.
author: NickSelin
manager: kfend
ms.date: 12/10/2019
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

# <a name="NUMERALSTOTEXT">NUMERALSTOTEXT Function</a>

[!include [banner](../includes/banner.md)]

The `NUMERALSTOTEXT` function returns a *String* representation of the specified number after it has been convered to text strings and spelled out in the specified language.

## Syntax

```
NUMERALSTOTEXT (number, language, currency, print currency name flag, decimal points)
```

## Arguments

`number` : *Integer* or *Real*

A numeric value of the specified number that must be spelled out.

`language` : *String*

A *String* value representing the language code.

`currency` : *String*

A *String* value representing the currency code.

`print currency name flag` : *Boolean*

A *Boolean* value to indicate whether a currency name must be added to the spelled-out text.

`decimal points` : *Integer*

An *Integer* value to indicate the number of decimals for the spelled-out text.

## Returns

*String*

The result text value.

## Usage notes

The language code is optional. When it's defined as an empty string, the language code for the running context is used. The default language code is EN-US. The language code for the running context is defined in a **Folder** or **File** element of the ER format that is running.

The currency code is optional. When it's defined as an empty string, the company currency for the running context is used.

> [!NOTE] 
> The **print currency name flag** and **decimal points parameters** are analyzed only for the following language codes: CS, ET, HU, LT, LV, PL, and RU. Additionally, the **print currency name flag** parameter is only analyzed for companies where the country's or region's context supports declension of currency names.

## Example 1

`NUMERALSTOTEXT (1234.56, "EN-US", "", false, 2)` returns **"One Thousand Two Hundred Thirty Four and 56"**.

## Example 2

`NUMERALSTOTEXT (120, "PL", "", false, 0)` returns **"Sto dwadzieścia"**. 

## Example 3

`NUMERALSTOTEXT (120.21, "RU", "EUR", true, 2)` returns **"Сто двадцать евро 21 евроцент"**.

## Additional resources

[Text functions](er-functions-category-text.md)
