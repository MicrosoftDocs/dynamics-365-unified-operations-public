---
# required metadata

title: List of ER functions of the logical category
description: This topic explains what logical functions are supported in ER
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

# Logical functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) logical functions can be used to work with logical values for carrying out more than one comparison in a single expression or testing multiple conditions. You can find a summary of such functions below in this article.

## List of supported functions

| **Function**  | **Description**  |
|---------------|------------------|
| [And](er-functions-logical-and.md)                       | Returns a *Boolean* **TRUE** if all specified conditions are true. Otherwise, return a *Boolean* **FALSE**.             |
| [Case](er-functions-logical-case.md)                     | Evaluates the value of the specified expression against the specified alternative options. Returns the result of the first option that equals the value of the specified expression. Otherwise, returns an optional default result, if a default result is specified as the last argument of the called function that is not preceded by an option. Returned value can be a value of any of the supported data types.             |
| [If](er-functions-logical-if.md)                         | Returns the first specified value when the specified condition is met. Otherwise, return the second specified value. Returned value can be a value of any of the supported data types.   |
| [Not](er-functions-logical-not.md)                       | Returns the reversed logical value of the specified condition as a *Boolean* value.                                      |
| [Or](er-functions-logical-or.md)                         | Returns a *Boolean* **FALSE** if all specified conditions are false. Return a *Boolean* **TRUE** if any specified condition is true.                                                   |
| [ValueIn](er-functions-logical-valuein.md)               | Determines whether the specified input matches any value of a given item in the specified list. Return a *Boolean* **TRUE** if the specified input matches the result of running the specified expression for at least one record of the specified list. Otherwise, return a *Boolean* **FALSE**.             |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)
