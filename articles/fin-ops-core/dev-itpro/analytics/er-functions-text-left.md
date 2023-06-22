---
title: LEFT ER function
description: This article provides information about how the LEFT Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/11/2019
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

# LEFT ER function

[!include [banner](../includes/banner.md)]

The `LEFT` function returns a *String* value that presents the specified number of characters from the start of the specified string.

## Syntax

```vb
LEFT (text, number)
```

## Arguments

`text`: *String*

A *String* value that represents the original text.

`number`: *Integer*

The number of characters that must be returned from the start of the original text.

## Return values

*String*

The resulting text value.

## Example

`LEFT ("Sample", 3)` returns **"Sam"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
