---
title: EMPTYRECORD ER function
description: This article provides information about how the EMPTYRECORD Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/12/2019
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

# EMPTYRECORD ER function

[!include [banner](../includes/banner.md)]

The `EMPTYRECORD` function returns a null *Container (record)* value that has the same structure as the specified record list or record.

## Syntax

```vb
EMPTYRECORD (list)
```

## Arguments

`list`: *Record list* or *Container (record)*

The valid path of a data source of either the *Record list* or *Container (record)* type.

## Return values

*Container (record)*

The resulting record value.

## Usage notes

> [!NOTE] 
> A null record is a record where all fields have an empty value. An empty value is **0** (zero) for numbers, an empty string for strings, and so on.

## Example

`EMPTYRECORD (SPLIT ("abc", 1))` returns a new empty record that has the same structure as the list that is returned by the `SPLIT` function. For more information, see [SPLIT](er-functions-list-split.md).

## Additional resources

[Record functions](er-functions-category-record.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
