---
# required metadata

title: TABLENAME2ID ER function
description: This topic provides information about how the TABLENAME2ID Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/12/2019
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

# <a name="TABLENAME2ID">TABLENAME2ID ER function</a>

[!include [banner](../includes/banner.md)]

The `TABLENAME2ID` function returns a numeric representation of the table ID for the specified table name as an *Integer* value.

## Syntax

```vb
TABLENAME2ID (text)
```

## Arguments

`text`: *String*

A text value that represents a valid table name.

## Return values

*Integer*

The resulting numeric value.

## Usage notes

Execution of this function can have different results in different instances of Microsoft Dynamics 365 Finance, even if the same company name is used.

## Example

`TABLENAME2ID ("Intrastat")` returns **1510**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
