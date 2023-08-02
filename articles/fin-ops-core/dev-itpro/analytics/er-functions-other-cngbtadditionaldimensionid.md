---
title: CN_GBT_ADDITIONALDIMENSIONID ER function
description: This article provides information about how the CN_GBT_ADDITIONALDIMENSIONID Electronic reporting (ER) function is used.
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

# CN_GBT_ADDITIONALDIMENSIONID ER function

[!include [banner](../includes/banner.md)]

The `CN_GBT_ADDITIONALDIMENSIONID` function returns a *String* value that represents a single financial dimension ID that is taken from the specified string. The specified string presents all dimensions as a comma-separated list of IDs.

## Syntax

```vb
CN_GBT_ADDITIONALDIMENSIONID (text, number)
```

## Arguments

`text`: *String*

A *String* value that presents all dimensions as a comma-separated list of IDs.

`number`: Integer

An *Integer* value that defines the sequence code of the requested dimension in the specified string.

## Return values

*String*

The resulting text value.

## Example

`CN_GBT_AdditionalDimensionID ("AA,BB,CC,DD,EE,FF,GG,HH", 3)` returns **"CC"**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
