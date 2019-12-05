---
# required metadata

title: COUNTIF ER function
description: This topic provides information about how the COUNTIF ER function is used.
author: NickSelin
manager: kfend
ms.date: 12/05/2019
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

# <a name="COUNTIF">COUNTIF Function</a>

[!include [banner](../includes/banner.md)]

The `COUNTIF` function returns an *Integer* value as the number of format elements that was collected at their usage to generate an outbound document during the format run, and that satisfies the specified condition consisting of a key range and a key value.

## Syntax

```
COUNTIF (condition range, condition value)
```

## Arguments

`condition range` : *String*

A value which is returned by the expression that has been configured in the **Collected data key name** property of an ER format component.

`condition value` : *String*

A value which is returned by the expression that has been configured in the **Collected data key value** property of an ER format component.

## Returns

*Integer*

The result numeric value.

## Usage notes

The **Collected data key name** and **Collected data key value** property can be configured for either the **Sequence** or **XML Element** component of an ER format that resides under the **Common \\ File** component the **Collect output
details** option which is turned on.

Returns a **0** (zero) value when the **Collect output details** flag of the current **Common \\ File** component is turned off.

The wildcard “\*” can be used in a **condition value** argument to represent any multiple characters.

The wildcard “\*” can be used in a **condition range** argument to represent any multiple characters.

## Example

To learn more about how to use this function, see the task guide, [ER Use data of format output for counting and summing](tasks/er-format-counting-summing-1.md), which is part of the **Acquire/Develop IT service/solution components**
business process.

## Additional resources

[Data collection functions](er-functions-category-data-collection.md)
