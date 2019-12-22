---
# required metadata

title: ALLITEMS ER function
description: This topic provides information about how the ALLITEMS Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/04/2019
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

# <a name="ALLITEMS">ALLITEMS ER function</a>

[!include [banner](../includes/banner.md)]

The `ALLITEMS` function runs as an in-memory selection and returns a new flattened *Record list* value as a list of records that represents all items that match the specified path.

## Syntax

```
ALLITEMS (path)
```

## Arguments

`path`: *Record list*

The valid path of a data source of the *Record list* data type.

## Return values

*Record list*

The resulting list of records.

## Usage notes

The path must be defined as a valid data source path of a data source element of the *Record list* data type. Data elements such as the path string and date should raise an error in the Electronic reporting (ER) expression builder at design time.

We don't recommend that you use this function for transactional data sources that might contain a large volume of data. Instead, consider using the [ALLTEMSQUERY](er-functions-list-allitemsquery.md) function.

## Example 1

If you enter `SPLIT("abcdef" , 2)` as data source **DS**, the expression `COUNT( ALLITEMS (DS))` returns **3**.

## Example 2

If you enter **Vend** as the data source of the *Record list* data type that refers to the VendTable application table, the expression `ALLITEMS (Vend.'<Relations'.ContactPerson)` returns a flattened list of records that has the **ContactPerson** table structure and contains all contact persons that can be accessed by using the **ContactPerson.ContactForParty == VendTable.Party** relation, and that is available for all vendors from the referenced vendor table.

## Additional resources

[List functions](er-functions-category-list.md)
