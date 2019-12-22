---
# required metadata

title: SUMIFS ER function
description: This topic provides information about how the SUMIFS Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# <a name="SUMIFS">SUMIFS ER function</a>

[!include [banner](../includes/banner.md)]

The `SUMIFS` function returns a *Real* value that represents the sum of values that were returned by bindings of format elements and collected when the format elements were used to generate an outbound document during the format run, and that satisfies the specified conditions. Each condition consists of a key range and a key value.

## Syntax

```
SUMIFS (key name for summing, condition 1 range, condition 1 value[, condition 2 range, condition 2 value, …, condition N range, condition N value])
```

## Arguments

`key name for summing`: *String*

A value that is returned by the expression that has been configured in the **Collected data key name** property of the Electronic reporting (ER) format component for which the value of the binding must be used for summing purposes.

The **Collected data key name** property can be configured for either a **Numeric** component or a **String** component of an ER format that resides under the **Common\\File** component where the **Collect output details** option is turned on.

`condition 1 range`: *String*

A value that is returned by the expression that has been configured in the **Collected data key name** property of an ER format component. This argument is mandatory.

The **Collected data key name** property can be configured for either a **Sequence** component or an **XML Element** component of an ER format that resides under the **Common\\File** component where the **Collect output details** option is turned on.

`condition 1 value`: *String*

A value that is returned by the expression that has been configured in the **Collected data key value** property of an ER format component. This argument is mandatory.

The **Collected data key value** property can be configured for either a **Sequence** component or an **XML Element** component of an ER format that resides under the **Common\\File** component where the **Collect output details** option is turned on.

`condition N range`: *String*

A value that is returned by the expression that has been configured in the **Collected data key name** property of an ER format component. These additional arguments are optional.

The **Collected data key name** property can be configured for either a **Sequence** component or an **XML Element** component of an ER format that resides under the **Common\\File** component where the **Collect output details** option is turned on.

`condition N value`: *String*

A value that is returned by the expression that has been configured in the **Collected data key value** property of an ER format component. These additional arguments are optional.

The **Collected data key value** property can be configured for either a **Sequence** component or an **XML Element** component of an ER format that resides under the **Common\\File** component where the **Collect output details** option is turned on.

## Return values

*Real*

The resulting numeric value.

## Usage notes

This function returns a **0** (zero) value when the **Collect output details** option of the current **Common\\File** component is turned off.

In the `condition range` arguments, the wildcard character **"\*"** can be used to represent any multiple characters.

In the `condition value` arguments, the wildcard character **"\*"** can be used to represent any multiple characters.

## Example

For more information about how to use this function, see the [ER Use data of format output for counting and summing](tasks/er-format-counting-summing-1.md) task guide, which is part of the **Acquire/Develop IT service/solution components** business process.

## Additional resources

[Data collection functions](er-functions-category-data-collection.md)
