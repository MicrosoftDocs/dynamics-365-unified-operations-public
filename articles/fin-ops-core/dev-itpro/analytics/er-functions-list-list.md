---
# required metadata

title: LIST ER function
description: This topic provides information about how the LIST Electronic reporting (ER) function is used.
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

# <a name="LIST">LIST ER function</a>

[!include [banner](../includes/banner.md)]

The `LIST` function returns a *Record list* value that consists of a new list of records that is created from the specified arguments.

## Syntax

```
LIST (record 1 [, record 2, …, record N])
```

## Arguments

`record 1`: *Container (record)*

A reference to a data source of the *Record* data type. This argument is required.

`record N`: *Container (record)*

A reference to a data source of the *Record* data type. These additional arguments are optional.

## Return values

*Record list*

The resulting list of records.

## Usage notes

The structure of the list that is created contains only the fields that are presented in the structure of every record that is mentioned in the arguments.

## Example

You enter data source **Record 1** of the *Container* type. This data source contains the following nested fields of the *Calculated field* type:

- **Code:** This field contains an expression that returns a value of the *String* type.
- **Amount:** This field contains an expression that returns a value of the *Real* type.

You then enter data source **Record 2** of the *Container* type. This data source contains the following nested fields of the *Calculated field* type:

- **Amount:** This field contains an expression that returns a value of the *Real* type.
- **IsValid:** This field contains an expression that returns a value of the *Boolean* type.

In this case, the expression `LIST('Record 1', 'Record 2')` returns a new list that contains two records. The structure of this list consists of a single **Amount** field of the *Real* type, because this field is the only field that is presented in every argument of the called function.

## Additional resources

[List functions](er-functions-category-list.md)
