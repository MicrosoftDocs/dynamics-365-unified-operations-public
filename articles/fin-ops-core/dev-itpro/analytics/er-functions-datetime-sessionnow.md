---
title: SESSIONNOW ER function
description: Learn about how the SESSIONNOW Electronic reporting (ER) function is used, including syntax strings, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 12/04/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# SESSIONNOW ER function

[!include [banner](../includes/banner.md)]

The `SESSIONNOW` function returns a *DateTime* value that represents the current application session date and time.

## Syntax

```vb
SESSIONNOW ()
```

## Return values

*DateTime*

The resulting date/time value.

## Example

`DATETIMEFORMAT (SESSIONNOW(), "d", "DE")` returns the current application session date/time value, December 24, 2015, as **"24.12.2015"**, based on the selected German culture and the specified format.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
