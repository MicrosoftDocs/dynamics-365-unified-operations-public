---
title: List of ER functions in the data collection category
description: This article provides information about the data collection functions that are supported in Electronic reporting (ER).
author: kfend
ms.date: 12/04/2019
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

# List of ER functions in the data collection category

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) data collection functions are used to do counting and summing in an ER format that is being run, based on data of the output that has already been generated in **Text** or **Xml** format. This approach is used to help improve performance of an ER format that is run, to enter values of running totals in generated documents, and for other purposes. This article provides a summary of these functions.

## List of supported functions

| Function | Description |
|----------|-------------|
| [CollectedList](er-functions-datacollection-collectedlist.md) | This function returns a *Record list* value that contains the list of values that were returned by the **Collected data key value** property of format elements and collected when the format elements were used to generate an outbound document during the format run, and that satisfies the specified conditions. Each condition consists of a key range and a key value. |
| [CountIF](er-functions-datacollection-countif.md) | This function returns an *Integer* value that represents the number of format elements that was collected when the format elements were used to generate an outbound document during the format run, and that satisfies the specified condition. The condition consists of a key range and a key value. |
| [CountIFs](er-functions-datacollection-countifs.md) | This function returns an *Integer* value that represents the number of format elements that was collected when the format elements were used to generate an outbound document during the format run, and that satisfies the specified conditions. Each condition consists of a key range and a key value. |
| [FormatElementName](er-functions-datacollection-formatelementname.md) | This function returns a *String* value that represents the name of the current ER format's element. |
| [SumIF](er-functions-datacollection-sumif.md) | This function returns a *Real* value that represents the sum of values that were returned by bindings of format elements and collected when the format elements were used to generate an outbound document during the format run, and that satisfies the specified condition. The condition consists of a key range and a key value. |
| [SumIFs](er-functions-datacollection-sumifs.md) | This function returns a *Real* value that represents the sum of values that were returned by bindings of format elements and collected when the format elements were used to generate an outbound document during the format run, and that satisfies the specified conditions. Each condition consists of a key range and a key value. |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
