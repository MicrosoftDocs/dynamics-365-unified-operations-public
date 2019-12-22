---
# required metadata

title: CURCREDREF ER function
description: This topic provides information about how the CURCREDREF Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/17/2019
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

# <a name="CURCREDREF">CURCREDREF ER function</a>

[!include [banner](../includes/banner.md)]

The `CURCREDREF` function returns a *String* value that represents a creditor reference, based on the digits of the specified invoice number.

## Syntax

```
CURCREDREF (invoice number digits)
```

## Arguments

`invoice number digits`: *String*

A text value that represents the digits of an invoice number.

## Return values

*String*

The resulting text value.

## Example

`CURCredRef ("VEND-200002")` returns **"2200002"**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
