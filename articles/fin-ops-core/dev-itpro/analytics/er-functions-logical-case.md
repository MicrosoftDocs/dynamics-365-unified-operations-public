---
# required metadata

title: CASE ER function
description: This topic explains how the CASE ER function is used
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

# <a name="CASE">CASE Function</a>

[!include [banner](../includes/banner.md)]

The `CASE` function evaluates the value of the specified expression against the specified alternative options. Returns the result of the first option that equals the value of the specified expression. Otherwise, return an optional default result, if a default result is specified as the last argument of the called function that is not preceded by an option.

## Syntax

```
CASE (expression, option 1, result 1 [, option 2, result 2, … , option N, result N, default result])
```

## Arguments

`expression` : *Primitive data type* (boolean, numeric or text)

A valid expression returning a value of the primitive data type.

`option 1` : *Primitive data type* (boolean, numeric or text)

A valid expression returning a value of the same primitive data type as the first argument of the called function. This argument is mandatory.

`result 1` : *Any of the supported data types*

The returned result corresponding to the preceding option. This argument is mandatory.

`option N` : *Primitive data type* (boolean, numeric or text)

A valid expression returning a value of the same primitive data type as the first argument of the called function. This argument is optional.

`result N` : *Any of the supported data types*

The returned result corresponding to the preceding option. This argument is optional.

`default result` : *Any of the supported data types*

The result returning if there is no match. This argument is optional.

## Returns

*Any of the supported data types*

The result value of any of the supported data types.

## Usage notes

An exception is thrown at runtime if there is no match and an optional default value is not defined.

All results must be specified by using the same data type. An exception is thrown at design time when data types of configured results do not match.

If the first result value and the Nth result value are values of the *Container (record)* or *Record list* data types, the result has only the fields that exist in both values.

## Example

`CASE( DATETIMEFORMAT( NOW(), "MM"), "10", "WINTER", "11", "WINTER", "12", "WINTER", "")` returns the string "WINTER" when the current application session date is between October and December. Otherwise, it returns a blank string.

## Additional resources

[Logical functions](er-functions-category-logical.md)
