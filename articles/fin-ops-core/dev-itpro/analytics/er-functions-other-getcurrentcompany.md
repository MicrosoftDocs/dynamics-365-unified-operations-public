---
title: GETCURRENTCOMPANY ER function
description: This article provides information about how the GETCURRENTCOMPANY Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/17/2019
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

# GETCURRENTCOMPANY ER function

[!include [banner](../includes/banner.md)]

The `GETCURRENTCOMPANY` function returns a *String* value that represents the code for the legal entity (company) that a user is currently signed in to.

## Syntax

```vb
GETCURRENTCOMPANY ()
```

## Return values

*String*

The resulting text value.

## Example

`GETCURRENTCOMPANY ()` returns **USMF** for a user who is signed in to the **Contoso Entertainment System USA** company.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
