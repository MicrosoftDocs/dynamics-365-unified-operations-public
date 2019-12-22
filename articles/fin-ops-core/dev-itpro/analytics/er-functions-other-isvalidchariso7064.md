---
# required metadata

title: ISVALIDCHARACTERISO7064 ER function
description: This topic provides information about how the ISVALIDCHARACTERISO7064 Electronic reporting (ER) function is used.
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

# <a name="ISVALIDCHARACTERISO7064">ISVALIDCHARACTERISO7064 ER function</a>

[!include [banner](../includes/banner.md)]

The `ISVALIDCHARACTERISO7064` function returns a *Boolean* value of **TRUE** if the specified string represents a valid international bank account number (IBAN). Otherwise, it returns a *Boolean* value of **FALSE**.

## Syntax

```
ISVALIDCHARACTERISO7064 (text)
```

## Arguments

`text`: *String*

A text value that represents an IBAN.

## Return values

*String*

The resulting text value.

## Example

`ISVALIDCHARACTERISO7064 ("AT61 1904 3002 3457 3201")` returns **TRUE**. 

`ISVALIDCHARACTERISO7064 ("AT61")` returns **FALSE**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
