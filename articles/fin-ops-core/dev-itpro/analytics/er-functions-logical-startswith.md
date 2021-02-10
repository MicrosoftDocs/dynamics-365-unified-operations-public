---
# required metadata

title: STARTSWITH ER function
description: This topic provides information about how the STARTSWITH Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 02/03/2021
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

# STARTSWITH ER function

[!include [banner](../includes/banner.md)]

The `STARTSWITH` function determines whether the specified input starts with a specified text. It returns a *Boolean* value of **TRUE** if the specified input starts with a specified text. Otherwise, it returns a *Boolean* value of **FALSE**.

## Syntax

```vb
STARTSWITH (input, start text)
```

## Arguments

`input`: *String*

The valid path of an item of a data source of the *String* type or a string constant the value of which might start with the second argument.

`start text`: *String*

The valid path of a data source of the *String* data type or a string constant the value of which might be at the beginning of the first argument.

## Return values

*Boolean*

The resulting *Boolean* value.

## Usage notes

Notice that this function can be used to specify a condition expression of the [FILTER](er-functions-list-filter.md) function only when the relevant mapping is configured in [Regulatory Configuration Services](https://docs.microsoft.com/dynamics365/finance/localizations/rcs-globalization-feature) to access [Microsoft Dataverse](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/data-integration-cds). Otherwise, the exception is thrown at design time suggesting to use the [WHERE](er-functions-list-where.md) function instead of the FILTER one.

## Example 1

The `STARTSWITH ("abc", "d")` expression returns **FALSE** while the `STARTSWITH ("abc", "A")` one returns **TRUE**.

## Example 2

The `STARTSWITH (model.InvoiceBase.Customer.PostalAddress.Address, "123 Coffee Street")` expression returns **TRUE** when the value of the **Address** field of the **model** data source starts with the **123 Coffee Street** characters. Otherwise, it returns **FALSE**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
