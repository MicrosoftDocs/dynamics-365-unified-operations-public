---
title: STRINGJOIN ER function
description: This article provides information about how the STRINGJOIN Electronic reporting (ER) function is used.
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

# STRINGJOIN ER function

[!include [banner](../includes/banner.md)]

The `STRINGJOIN` function returns a *String* value that consists of concatenated values of the specified field from the specified list. The values can be separated by the specified delimiter.

## Syntax

```vb
STRINGJOIN (list, field, delimiter)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

`field`: *Field*

The valid path of a field of the *String* data type in the specified list.

`delimiter`: *String*

A delimiter that is used to separate substrings.

## Return values

*String*

The resulting text value.

## Example

If you enter `SPLIT("abc" , 1)` as data source **DS**, the expression `STRINGJOIN (DS, DS.Value, "-")` returns **"a-b-c"**.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
