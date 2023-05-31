---
title: CASE ER function
description: This article provides information about how the CASE Electronic reporting (ER) function is used.
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

# CASE ER function

[!include [banner](../includes/banner.md)]

The `CASE` function evaluates the value of the specified expression against the specified alternative options and returns the result of the first option that equals the value of the specified expression. Otherwise, it returns the optional default result, if a default result is specified as the last argument of the called function that isn't preceded by an option. The value that is returned can be a value of any of the supported data types.

## Syntax

```vb
CASE (expression, option 1, result 1[, option 2, result 2, …, option N, result N, default result])
```

## Arguments

`expression`: *Primitive data type* (Boolean, numeric, or text)

A valid expression that returns a value of the primitive data type.

`option 1`: *Primitive data type* (Boolean, numeric, or text)

A valid expression that returns a value of the same primitive data type as the `expression` argument of the called function. This argument is required.

`result 1`: *Any of the supported data types*

The returned result that corresponds to the preceding option. This argument is required.

`option N`: *Primitive data type* (Boolean, numeric, or text)

A valid expression that returns a value of the same primitive data type as the `expression` argument of the called function. This argument is optional.

`result N`: *Any of the supported data types*

The returned result that corresponds to the preceding option. This argument is optional.

`default result`: *Any of the supported data types*

The result that should be returned if there is no match. This argument is optional.

## Return values

*Any of the supported data types*

The resulting value of any of the supported data types.

## Usage notes

An exception is thrown at runtime if there is no match and an optional default result isn't defined.

All results must be specified by using the same data type. An exception is thrown at design time if the data types of the configured results don't match.

If the first result value and the *N*th result value are values of the *Container (record)* or *Record list* data type, the result has only the fields that exist in both values.

## Example

`CASE( DATETIMEFORMAT( NOW(), "MM"), "10", "WINTER", "11", "WINTER", "12", "WINTER", "")` returns the string **"WINTER"** if the current application session date is between October and December. Otherwise, it returns a blank string.

## Additional resources

[Logical functions](er-functions-category-logical.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
