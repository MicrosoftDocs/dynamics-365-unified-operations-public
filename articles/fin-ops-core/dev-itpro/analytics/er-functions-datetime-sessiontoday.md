---
title: SESSIONTODAY ER function
description: Learn about how the SESSIONTODAY Electronic reporting (ER) function is used, including syntax strings, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 12/05/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# SESSIONTODAY ER function

[!include [banner](../includes/banner.md)]

The `SESSIONTODAY` function returns a *Date* value that represents the current application session date.

## Syntax

```vb
SESSIONTODAY ()
```

## Return values

*Date*

The resulting date value.

## Example

`DATEFORMAT (SESSIONTODAY (), "d", "DE")` returns the current application session date, December 24, 2015, as the string **"24-12-2015"**, based on the selected German culture and the specified format.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
