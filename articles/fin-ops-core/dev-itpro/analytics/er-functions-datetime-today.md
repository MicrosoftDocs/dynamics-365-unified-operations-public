---
title: TODAY ER function
description: This article provides information about how the TODAY Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/05/2019
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

# TODAY ER function

[!include [banner](../includes/banner.md)]

The `TODAY` function returns a *Date* value that represents the current application server date.

## Syntax

```xpp
TODAY ()
```

## Return values

*Date*

The resulting date value.

## Example

`DATEFORMAT (TODAY (), "dd-MM-yyyy")` returns the current application server date, December 24, 2015, as the string **"24-12-2015"**, based on the specified custom format.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
