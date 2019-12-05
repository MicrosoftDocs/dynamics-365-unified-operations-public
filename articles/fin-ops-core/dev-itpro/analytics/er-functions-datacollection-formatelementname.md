---
# required metadata

title: FORMATELEMENTNAME ER function
description: This topic provides inofrmation about how the FORMATELEMENTNAME ER function is used.
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

# <a name="FORMATELEMENTNAME">FORMATELEMENTNAME Function</a>

[!include [banner](../includes/banner.md)]

The `FORMATELEMENTNAME` function returns a *String* value of the name of the current ER format's element.

## Syntax

```
FORMATELEMENTNAME ()
```

## Returns

*String*

The result text value.

## Usage notes

This function can be called in ER expressions that were configured for the **Collected data key name** and **Collected data key value** property of an ER format component from the **Text** group that reside under the **Common \\ File** component the **Collect output details** flag which is turned on.

## Example

To learn more about how to use this function, see the task guide, [ER Use data of format output for counting and summing](tasks/er-format-counting-summing-1.md), which is part of the **Acquire/Develop IT service/solution components**
business process.

## Additional resources

[Data collection functions](er-functions-category-data-collection.md)
