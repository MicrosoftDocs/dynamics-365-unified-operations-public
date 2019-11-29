---
# required metadata

title: NULLCONTAINER ER function
description: This topic explains how the NULLCONTAINER ER function is used
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

# <a name="NULLCONTAINER">NULLCONTAINER Function</a>

[!include [banner](../includes/banner.md)]

The `NULLCONTAINER` function returns a null *Container (record)* that has the same structure as the specified record list or record.

## Syntax

```
NULLCONTAINER (list)
```

## Arguments

`list` : *Record list* or *Container (record)*

A valid path to a data source of either *Record list* or *Container (record)* type.

## Returns

*Container (record)*

The result record value.

## Usage notes

> [!NOTE] This function is obsolete. Use
[EMPTYRECORD](er-functions-record-emptyrecord.md) instead.

## Example

`NULLCONTAINER (SPLIT ("abc", 1))` returns a new empty record that has the same structure as the list that is returned by the [SPLIT](er-functions-list-split.md) function.

## Additional resources

[Record functions](er-functions-category-record.md)
