---
title: CONTAINS ER function
description: Learn about how the CONTAINS Electronic reporting (ER) function is used, including syntax strings, arguments, return values, usage notes, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 02/11/2021
ms.custom: 
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-02-01
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 10.0.18
ms.assetid: 
---

# CONTAINS ER function

[!include [banner](../includes/banner.md)]

The `CONTAINS` function determines whether the specified input contains the specified text. It returns a *Boolean* value of **TRUE** if the specified input contains the specified text. Otherwise, it returns a *Boolean* value of **FALSE**.

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

This function can be used to specify a condition expression of the [FILTER](er-functions-list-filter.md) function only when the relevant mapping is configured in [Regulatory Configuration Services](../../../finance/localizations/rcs-globalization-feature.md) to access [Microsoft Dataverse](/power-platform/admin/data-integrator). Otherwise, an exception is thrown at design time. The message that you receive recommends that you use the [WHERE](er-functions-list-where.md) function instead of the `FILTER` function.

## Example 1

The expression `CONTAINS ("abc", "d")` returns **FALSE**, whereas the expression `CONTAINS ("abc", "C")` returns **TRUE**.

## Example 2

The expression `CONTAINS (model.InvoiceBase.Customer.PostalAddress.Address, "DEU")` returns **TRUE** if the value of the **Address** field of the **model** data source contains the string **DEU**. Otherwise, it returns **FALSE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
