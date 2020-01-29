---
# required metadata

title: CHAR ER function
description: This topic provides information about how the CHAR Electronic reporting (ER) function is used.
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

# <a name="CHAR">CHAR ER function</a>

[!include [banner](../includes/banner.md)]

The `CHAR` function returns a *String* value that presents a single character that is referenced by the specified Unicode number.

## Syntax

```vb
CHAR (number)
```

## Arguments

`number`: *Integer*

A number that corresponds to an expected single character.

## Return values

*String*

The resulting text value.

## Usage notes

The string that this function returns depends on the encoding that is selected in the parent **FILE** format element. For a list of the supported encodings, see [Encoding class](https://msdn.microsoft.com/library/system.text.encoding(v=vs.110).aspx).

## Example

`CHAR (255)` returns **"ÿ"**.

## Additional resources

[Text functions](er-functions-category-text.md)
