---
# required metadata

title: IF ER function
description: This topic explains how the IF ER function is used
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

# <a name="IF">IF Function</a>

[!include [banner](../includes/banner.md)]

The `IF` function returns the first specified value when the specified condition is met. Otherwise, return the second specified value. Returned value can be a value of any of the supported data types.

## Syntax

```
IF (condition, first value, second value) as any of the supported data types
```

## Arguments

`condition` : *Boolean*

A valid conditional expression to be tested.

`first value` : *Any of the supported data types*

The result returned when the condition is met.

`second value` : *Any of the supported data types*

The result returned when the condition is not met.

## Returns

*Any of the supported data types*

The result value of any of the supported data types.

## Usage notes

First and second value arguments must be specified by using the same data type. An exception is thrown at design time when data types of configured values do not match.

If the first value and the second value are values of the *Container (record)* or *Record list* data types, the result has only the fields that exist in both values.

## Example

`IF (1=2, "condition is met", "condition is not met")` returns the string "condition is not met".

## Additional resources

[Logical functions](er-functions-category-logical.md)
