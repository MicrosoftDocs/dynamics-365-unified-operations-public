---
# required metadata

title: LIST ER function
description: This topic provides information about how the LIST ER function is used.
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

# <a name="LIST">LIST Function</a>

[!include [banner](../includes/banner.md)]

The `LIST` function returns a *Record list* as a new list of records that is created from specified arguments.

## Syntax

```
LIST (record 1 [, record 2, … , record N])
```

## Arguments

`record 1` : *Container (record)*

A reference to a data source of the *Record* data type. One argument is mandatory.

`record N` : *Container (record)*

A reference to a data source of the *Record* data type. Other arguments are optional.

## Returns

*Record list*

The result list of records.

## Usage notes

The structure of the created list contains the only fields that are presented in the structure of every record that is mentioned in arguments.

## Example

You can enter the data source **Record 1** of the `Container` type containing the following nested fields of the `Calculated field` type:

-	**Code**: Contains the expression that returns the value of the `String` type
-	**Amount**: Contains the expression that returns the value if the `Real` type

Then, you can enter the data source **Record 2** of the `Container` type containing the following nested fields of the `Calculated field` type:

-	**Amount**: Contains the expression that returns the value if the `Real` type
-	**IsValid**: Contains the expression that returns the value of the `Boolean` type

The expression `LIST(‘Record 1’, ‘Record 2’)` returns a new list that contains two records and has a structure that consists of a single field **Amount** of the `Real` type and is the only field is presented in every argument of the called function.

## Additional resources

[List functions](er-functions-category-list.md)
