---
title: List of ER functions in the logical category
description: This article provides information about the logical functions that are supported in Electronic reporting (ER).
author: kfend
ms.date: 02/11/2021
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

# List of ER functions in the logical category

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) logical functions can be used to work with logical values to perform more than one comparison in a single expression or test multiple conditions. This article provides a summary of these functions.

## List of supported functions

| Function | Description |
|----------|-------------|
| [And](er-functions-logical-and.md)                       | This function returns a *Boolean* value of **TRUE** if all the specified conditions are true. Otherwise, it returns a *Boolean* value of **FALSE**. |
| [Case](er-functions-logical-case.md)                     | This function evaluates the value of the specified expression against the specified alternative options and returns the result of the first option that equals the value of the specified expression. Otherwise, it returns an optional default result, if a default result is specified as the last argument of the called function that isn't preceded by an option. The value that is returned can be a value of any of the supported data types. |
| [Contains](er-functions-logical-contains.md)             | This function determines whether the specified input contains the specified text. It returns a *Boolean* value of **TRUE** if the specified input contains the specified text. Otherwise, it returns a *Boolean* value of **FALSE**. |
| [EndsWith](er-functions-logical-endswith.md)             | This function determines whether the specified input ends with the specified text. It returns a *Boolean* value of **TRUE** if the specified input ends with the specified text. Otherwise, it returns a *Boolean* value of **FALSE**. |
| [If](er-functions-logical-if.md)                         | This function returns the first specified value if the specified condition is met. Otherwise, it returns the second specified value. The value that is returned can be a value of any of the supported data types. |
| [Not](er-functions-logical-not.md)                       | This function returns the reversed logical value of the specified condition as a *Boolean* value. |
| [Or](er-functions-logical-or.md)                         | This function returns a *Boolean* value of **FALSE** if all the specified conditions are false. If any specified condition is true, the function returns a *Boolean* value of **TRUE**. |
| [StartsWith](er-functions-logical-startswith.md)         | This function determines whether the specified input starts with the specified text. It returns a *Boolean* value of **TRUE** if the specified input starts with the specified text. Otherwise, it returns a *Boolean* value of **FALSE**. |
| [ValueIn](er-functions-logical-valuein.md)               | This function determines whether the specified input matches any value of a specified item in the specified list. It returns a *Boolean* value of **TRUE** if the specified input matches the result of running the specified expression for at least one record of the specified list. Otherwise, it returns a *Boolean* value of **FALSE**. |
| [ValueInLarge](er-functions-logical-valueinlarge.md)     | This function determines whether the specified input of the *Int64* or *Integer* type matches any value of a specified item in the specified list. It returns a *Boolean* value of **TRUE** if the specified input matches the result of running the specified expression for at least one record of the specified list. Otherwise, it returns a *Boolean* value of **FALSE**. |


## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
