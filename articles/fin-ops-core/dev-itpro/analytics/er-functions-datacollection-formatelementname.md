---
title: FORMATELEMENTNAME ER function
description: This article provides information about how the FORMATELEMENTNAME Electronic reporting (ER) function is used.
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

# FORMATELEMENTNAME ER function

[!include [banner](../includes/banner.md)]

The `FORMATELEMENTNAME` function returns a *String* value that represents the name of the current Electronic reporting (ER) format's element.

## Syntax

```vb
FORMATELEMENTNAME ()
```

## Return values

*String*

The resulting text value.

## Usage notes

This function can be called in ER expressions that were configured for the **Collected data key name** and **Collected data key value** properties of an ER format component from the **Text** group that resides under the **Common\\File** component where the **Collect output details** option is turned on.

## Example

For more information about how to use this function, see the [ER Use data of format output for counting and summing](tasks/er-format-counting-summing-1.md) task guide, which is part of the **Acquire/Develop IT service/solution components** business process.

## Additional resources

[Data collection functions](er-functions-category-data-collection.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
