---
# required metadata

title: ENDSWITH ER function
description: This topic provides information about how the ENDSWITH Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 02/11/2021
ms.prod: 
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

# ENDSWITH ER function

[!include [banner](../includes/banner.md)]

The `ENDSWITH` function determines whether the specified input ends with the specified text. It returns a *Boolean* value of **TRUE** if the specified input ends with the specified text. Otherwise, it returns a *Boolean* value of **FALSE**.

## Syntax

```vb
ENDSWITH (input, end text)
```

## Arguments

`input`: *String*

The valid path of an item of a data source of the *String* type or a string constant, the value of which might end with the second argument.

`start text`: *String*

The valid path of a data source of the *String* data type or a string constant, the value of which might be at the end of the first argument.

## Return values

*Boolean*

The resulting *Boolean* value.

## Usage notes

This function can be used to specify a condition expression of the [FILTER](er-functions-list-filter.md) function only when the relevant mapping is configured in [Regulatory Configuration Services](../../../finance/localizations/rcs-globalization-feature.md) to access [Microsoft Dataverse](/power-platform/admin/data-integrator). Otherwise, an exception is thrown at design time. The message that you receive recommends that you use the [WHERE](er-functions-list-where.md) function instead of the `FILTER` function.

## Example 1

The expression `ENDSWITH ("abc", "d")` returns **FALSE**, whereas the expression `ENDSWITH ("abc", "C")` returns **TRUE**.

## Example 2

The expression `ENDSWITH (model.InvoiceBase.Customer.PostalAddress.Address, "USA")` returns **TRUE** if the value of the **Address** field of the **model** data source ends with the string **USA**. Otherwise, it returns **FALSE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
