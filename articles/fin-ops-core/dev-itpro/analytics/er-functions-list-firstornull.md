---
# required metadata

title: FIRSTORNULL ER function
description: This topic explains how the FIRSTORNULL ER function is used
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

# <a name="FIRSTORNULL">FIRSTORNULL Function</a>

[!include [banner](../includes/banner.md)]

The `FIRSTORNULL` returns the first record of the specified list as a *Container (record)*, if that record is not empty. Otherwise, returns a null *Container (record)*.

## Syntax

```
FIRSTORNULL (list)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

## Returns

*Container (record)*

The result record value.

## Example

The `FIRSTORNULL(SPLIT("",1)).Value` expression returns an empty string “”.

## Additional resources

[List functions](er-functions-category-list.md)
