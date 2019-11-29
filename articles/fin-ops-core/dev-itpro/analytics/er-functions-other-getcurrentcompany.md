---
# required metadata

title: GETCURRENTCOMPANY ER function
description: This topic explains how the GETCURRENTCOMPANY ER function is used
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

# <a name="GETCURRENTCOMPANY">GETCURRENTCOMPANY Function</a>

[!include [banner](../includes/banner.md)]

The `GETCURRENTCOMPANY` function returns a *String* value as representation of the code for the legal entity (company) that a user is currently signed in to.

## Syntax

```
GETCURRENTCOMPANY ()
```

## Returns

*String*

The result text value.

## Example

`GETCURRENTCOMPANY ()` returns **USMF** for a user who is signed in to the **Contoso Entertainment System USA** company.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)
