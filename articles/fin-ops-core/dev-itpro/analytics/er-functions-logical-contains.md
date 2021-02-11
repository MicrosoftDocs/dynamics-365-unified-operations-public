---
# required metadata

title: CONTAINS ER function
description: This topic provides information about how the CONTAINS Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 02/11/2021
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
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: AX 10.0.18

---

# CONTAINS ER function

[!include [banner](../includes/banner.md)]

The `CONTAINS` function determines whether the specified input contains a specified text. It returns a *Boolean* value of **TRUE** if the specified input contains a specified text. Otherwise, it returns a *Boolean* value of **FALSE**.

## Syntax

```vb
CONTAINS (input, search text)
```

## Arguments

`input`: *String*

The valid path of an item of a data source of the *String* type or a string constant, the value of which might contain the second argument.

`search text`: *String*

The valid path of a data source of the *String* data type or a string constant, the value of which might be contained in the first argument.

## Return values

*Boolean*

The resulting *Boolean* value.

## Usage notes

This function can be used to specify a condition expression of the [FILTER](er-functions-list-filter.md) function only when the relevant mapping is configured in [Regulatory Configuration Services](../../finance/localizations/rcs-globalization-feature.md) to access [Microsoft Dataverse](../data-entities/data-integration-cds.md). Otherwise, the exception is thrown at design time suggesting that you use the [WHERE](er-functions-list-where.md) function instead of the FILTER one.

## Example 1

The `CONTAINS ("abc", "d")` expression returns **FALSE** while the `CONTAINS ("abc", "C")` one returns **TRUE**.

## Example 2

The `CONTAINS (model.InvoiceBase.Customer.PostalAddress.Address, "DEU")` expression returns **TRUE** when the value of the **Address** field of the **model** data source contains the **DEU** characters. Otherwise, it returns **FALSE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
