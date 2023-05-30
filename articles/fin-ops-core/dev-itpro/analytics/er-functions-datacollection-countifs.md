---
title: COUNTIFS ER function
description: This article provides information about how the COUNTIFS Electronic reporting (ER) function is used.
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

# COUNTIFS ER function

[!include [banner](../includes/banner.md)]

The `COUNTIFS` function returns an *Integer* value that represents the number of format elements that was collected when the format elements were used to generate an outbound document during the format run, and that satisfies the specified conditions. Each condition consists of a key range and a key value.

## Syntax

```vb
COUNTIFS (condition 1 range, condition 1 value[, condition 2 range, condition 2 value, …, condition N range, condition N value])
```

## Arguments

`condition 1 range`: *String*

A value that is returned by the expression that has been configured in the **Collected data key name** property of an Electronic reporting (ER) format component. This argument is mandatory.

`condition 1 value`: *String*

A value that is returned by the expression that has been configured in the **Collected data key value** property of an ER format component. This argument is mandatory.

`condition N range`: *String*

A value that is returned by the expression that has been configured in the **Collected data key name** property of an ER format component. These additional arguments are optional.

`condition N value`: *String*

A value that is returned by the expression that has been configured in the **Collected data key value** property of an ER format component. These additional arguments are optional.

## Return values

*Integer*

The resulting numeric value.

## Usage notes

The **Collected data key name** and **Collected data key value** properties can be configured for either the **Sequence** component or the **XML Element** component of an ER format that resides under the **Common\\File** component where the **Collect output details** option is turned on.

This function returns a **0** (zero) value when the **Collect output details** option of the current **Common\\File** component is turned off.

In `condition range` arguments, the wildcard character **"\*"** can be used to represent any multiple characters.

In `condition value` arguments, the wildcard character **"\*"** can be used to represent any multiple characters.

## Example

For more information about how to use this function, see the [ER Use data of format output for counting and summing](tasks/er-format-counting-summing-1.md) task guide, which is part of the **Acquire/Develop IT service/solution components** business process.

## Additional resources

[Data collection functions](er-functions-category-data-collection.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
