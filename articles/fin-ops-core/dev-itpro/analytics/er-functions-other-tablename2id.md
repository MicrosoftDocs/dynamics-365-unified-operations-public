---
# required metadata

title: TABLENAME2ID ER function
description: This topic explains how the TABLENAME2ID ER function is used
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

# <a name="TABLENAME2ID">TABLENAME2ID Function</a>

[!include [banner](../includes/banner.md)]

The `TABLENAME2ID` function returns an *Integer* value as the numeric representation of a table ID for the specified table name.

## Syntax

```
TABLENAME2ID (text)
```

## Arguments

`text` : *String*

A text value representing a valid table name.

## Returns

*Integer*

The result numeric value.

## Usage notes

Note that the result of execution of this function can be different in different instances of Finance even the same company name is used.

## Example

`TABLENAME2ID ("Intrastat")` returns 1510.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
