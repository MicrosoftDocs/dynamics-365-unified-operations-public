---
title: ISVALIDCHARACTERISO7064 ER function
description: This article provides information about how the ISVALIDCHARACTERISO7064 Electronic reporting (ER) function is used.
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

# ISVALIDCHARACTERISO7064 ER function

[!include [banner](../includes/banner.md)]

The `ISVALIDCHARACTERISO7064` function returns a *Boolean* value of **TRUE** if the specified string represents a valid international bank account number (IBAN). Otherwise, it returns a *Boolean* value of **FALSE**.

## Syntax

```vb
ISVALIDCHARACTERISO7064 (text)
```

## Arguments

`text`: *String*

A text value that represents an IBAN.

## Return values

*String*

The resulting text value.

## Example

`ISVALIDCHARACTERISO7064 ("AT61 1904 3002 3457 3201")` returns **TRUE**. 

`ISVALIDCHARACTERISO7064 ("AT61")` returns **FALSE**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
