---
title: INDEX ER function
description: This article provides information about how the INDEX Electronic reporting (ER) function is used.
author: kfend
ms.date: 05/20/2021
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

# INDEX ER function

[!include [banner](../includes/banner.md)]

The `INDEX` function returns a *Container (record)* value that is selected by using the specified numeric index in the specified list. If the index is out of range for the records in the specified list, an exception is thrown.

## Syntax

```vb
INDEX (list, index)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

`index`: *Integer*

A numeric index that indicates the position of the desired record in the specified list.

> [!NOTE]
> Because one-based numbering is used for this function, specify the value **1** to return the first record of the specified list.

## Return values

*Container (record)*

The resulting record value.

## Example 1

If you enter data source **DS** of the *Calculated field* type, and it contains the expression `SPLIT ("A|B|C", "|")`, the expression `DS.Value` returns the text value **"B"** for the second record of this record list. The expression `INDEX (SPLIT ("A|B|C", "|"), 2).Value` also returns the text value **"B"**.

## Example 2

If you enter data source **DS** of the *Calculated field* type, and it contains the expression `SPLIT ("A|B|C", "|")`, the expression `INDEX (SPLIT ("A|B|C", "|"), 4).Value` throws an exception at runtime.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
