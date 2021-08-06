---
# required metadata

title: NULLCONTAINER ER function
description: This topic provides information about how the NULLCONTAINER Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 12/12/2019
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# NULLCONTAINER ER function

[!include [banner](../includes/banner.md)]

The `NULLCONTAINER` function returns a null *Container (record)* value that has the same structure as the specified record list or record.

## Syntax

```vb
NULLCONTAINER (list)
```

## Arguments

`list`: *Record list* or *Container (record)*

The valid path of a data source of either the *Record list* or *Container (record)* type.

## Return values

*Container (record)*

The resulting record value.

## Usage notes

> [!NOTE] 
> This function is obsolete. Use the `EMPTYRECORD` function instead. For more information, see [EMPTYRECORD](er-functions-record-emptyrecord.md).

## Example

`NULLCONTAINER (SPLIT ("abc", 1))` returns a new empty record that has the same structure as the list that is returned by the `SPLIT` function. For more information, see [SPLIT](er-functions-list-split.md).

## Additional resources

[Record functions](er-functions-category-record.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]