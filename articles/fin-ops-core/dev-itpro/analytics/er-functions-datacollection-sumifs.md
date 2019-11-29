---
# required metadata

title: SUMIFS ER function
description: This topic explains how the SUMIFS ER function is used
author: NickSelin
manager: kfend
ms.date: 11/29/2019
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

# <a name="SUMIFS">SUMIFS Function</a>

[!include [banner](../includes/banner.md)]

The `SUMIFS` function returns a *Real* value as the sum of values returned by bindings of format elements that was collected at their usage to generate outbound document during the format run, and that satisfies the specified conditions each of which consists of a key range and a key value.

## Syntax

```
SUMIFS (key name for summing, condition 1 range, condition 1 value [, condition 2 range, condition 2 value, … , condition N range, condition N value])
```

## Arguments

`key name for summing` : *String*

A value which is returned by the expression that has been configured in the **Collected data key name** property of an ER format component the value of binding of which must be used for summing.

The **Collected data key name** property can be configured for either **Numeric** or **String** component of an ER format that resides under the **Common \\ File** component the **Collect output details** option of which is turned on.

`condition 1 range` : *String*

A value which is returned by the expression that has been configured in the **Collected data key name** property of an ER format component. This argument is mandatory.

The **Collected data key name** property can be configured for either **Sequence** or **XML Element** component of an ER format that resides under the **Common \\ File** component the **Collect output details** option of which is turned on.

`condition 1 value` : *String*

A value which is returned by the expression that has been configured in the **Collected data key value** property of an ER format component. This argument is mandatory.

The **Collected data key value** property can be configured for either **Sequence** or **XML Element** component of an ER format that resides under the **Common \\ File** component the **Collect output details** option of which is turned on.

`condition N range` : *String*

A value which is returned by the expression that has been configured in the **Collected data key name** property of an ER format component. Other arguments are optional.

The **Collected data key name** property can be configured for either **Sequence** or **XML Element** component of an ER format that resides under the **Common \\ File** component the **Collect output details** option of which is turned on.

`condition N value` : *String*

A value which is returned by the expression that has been configured in the **Collected data key value** property of an ER format component. Other arguments are optional.

The **Collected data key value** property can be configured for either **Sequence** or **XML Element** component of an ER format that resides under the **Common \\ File** component the **Collect output details** option of which is turned on.

## Returns

*Real*

The result numeric value.

## Usage notes

Returns a **0** (zero) value when the **Collect output details** flag of the current **Common \\ File** component is turned off.

The wildcard “\*” can be used in a **condition value** argument to represent any multiple characters.

The wildcard “\*” can be used in a **condition range** argument to represent any multiple characters.

## Example

To learn more about how to use this function, see the [ER Use data of format output for counting and summing](tasks/er-format-counting-summing-1.md) task guide, which is part of the **Acquire/Develop IT service/solution components**
business process.

## Additional resources

[Data collection functions](er-functions-category-data-collection.md)
