---
title: MOD_97 ER function
description: This article provides information about how the MOD_97 Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/17/2019
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

# MOD_97 ER function

[!include [banner](../includes/banner.md)]

The `MOD_97` function returns a *String* value that represents a creditor reference as a MOD97 expression, based on the digits of the specified invoice number.

## Syntax

```vb
MOD_97 (invoice number digits)
```

## Arguments

`invoice number digits`: *String*

A text value that represents the digits of an invoice number.

## Return values

*String*

The resulting text value.

## Example

`MOD_97 ("VEND-200002")` returns **"20000285"**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
