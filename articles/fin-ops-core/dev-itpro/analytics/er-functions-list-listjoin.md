---
# required metadata

title: LISTJOIN ER function
description: This topic provides information about how the LISTJOIN Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 04/01/2020
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
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# <a name="LISTJOIN">LISTJOIN Function</a>

[!include [banner](../includes/banner.md)]

The `LISTJOIN` function returns a *Record list* value representing a new joined list of records that is created from the specified arguments.

## Syntax

```
LIST (list 1 [, list 2, … , list N])
```

## Arguments

`list 1` : *Record list*

A reference to a data source of the *Record list* data type. This argument is mandatory.

`list N` : *Record list*

A reference to a data source of the *Record list* data type. These additional arguments are optional.

## Returns

*Record list*

The resulting list of records.

## Usage notes

The structure of the list that is created contains only the fields that are presented in the structure of every record list that is mentioned in the arguments.

## Example

You enter the data source **Record 1** of the `Container`. This data source contains the following nested fields of the `Calculated field` type:

-	**Code**: This field contains an expression that returns a value of the the `String` type.
-	**Amount**: This field contains an expression that returns a value of the `Real` type.

You then enter data source **Record 2** of the `Container` type. This data source contains the following nested fields of the `Calculated field` type:

-	**Amount**: This field contains an expression that returns a value of the `Real` type.
-	**IsValid**: This field contains an expression that returns a value of the `Boolean` type.

In this case, the expression `LISTJOIN(LIST('Record 1'), LIST('Record 2'))` returns a new list that contains two records. The structure of this list consists of a single **Amount** field of the `Real` type, because this field is the only field that is presented in every argument of the called function.

## Additional resources

[List functions](er-functions-category-list.md)
