---
title: MOD_97 ER function
description: Learn about how the MOD_97 Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 12/17/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
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
