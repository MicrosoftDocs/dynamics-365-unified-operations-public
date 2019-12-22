---
# required metadata

title: IF ER function
description: This topic provides information about how the IF Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/12/2019
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

# <a name="IF">IF ER function</a>

[!include [banner](../includes/banner.md)]

The `IF` function returns the first specified value if the specified condition is met. Otherwise, it returns the second specified value. The value that is returned can be a value of any of the supported data types.

## Syntax

```
IF (condition, first value, second value) as any of the supported data types
```

## Arguments

`condition`: *Boolean*

A valid conditional expression that must be tested.

`first value`: *Any of the supported data types*

The result that is returned if the condition is met.

`second value`: *Any of the supported data types*

The result that is returned if the condition isn't met.

## Return values

*Any of the supported data types*

The resulting value of any of the supported data types.

## Usage notes

The `first value` and `second value` arguments must be specified by using the same data type. An exception is thrown at design time if the data types of the configured values don't match.

If the first value and the second value are values of the *Container (record)* or *Record list* data type, the result has only the fields that exist in both values.

## Example

`IF (1=2, "condition is met", "condition is not met")` returns the string **"condition is not met"**.

## Additional resources

[Logical functions](er-functions-category-logical.md)
