---
# required metadata

title: List of ER functions of the data collection category
description: This topic provides information about what data collection functions are supported in ER.
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

# Data collection functions

[!include [banner](../includes/banner.md)]

Electronic reporting (ER) data collection functions are used to do counting and summing in an executing ER format based on data of the already generated output in **Text** or **Xml** format. This approach is used to improve performance of an executed ER format, to populate to generated documents values of running totals, etc. You can find a summary of such functions below in this article.

## List of supported functions

| **Function** | **Description**                              |
|--------------|----------------------------------------------|
| [CollectedList](er-functions-datacollection-collectedlist.md) | Returns a *Record list* with the list of values returned by the **Collected data key value** property of format elements that was collected at their usage to generate outbound document during the format run, and that satisfies the specified conditions each of which consists of a key range and a key value. |
| [CountIF](er-functions-datacollection-countif.md) | Returns an *Integer* value as the number of format elements that was collected at their usage to generate outbound document during the format run, and that satisfies the specified condition consisting of a key range and a key value. |
| [CountIFs](er-functions-datacollection-countifs.md)           | Returns an *Integer* value as the number of format elements that was collected at their usage to generate outbound document during the format run, and that satisfies the specified conditions each of which consists of a key range and a key value.                                                          |
| [FormatElementName](er-functions-datacollection-formatelementname.md) | Returns a *String* value of the name of the current ER format's element.  |
| [SumIF](er-functions-datacollection-sumif.md)                 | Returns a *Real* value as the sum of values returned by bindings of format elements that was collected at their usage to generate outbound document during the format run, and that satisfies the specified condition consisting of a key range and a key value.                                                    |
| [SumIFs](er-functions-datacollection-sumifs.md)               | Returns a *Real* value as the sum of values returned by bindings of format elements that was collected at their usage to generate outbound document during the format run, and that satisfies the specified conditions each of which consists of a key range and a key value.                                      |

## Additional resources

[Electronic Reporting overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Electronic reporting formula language](er-formula-language.md)
