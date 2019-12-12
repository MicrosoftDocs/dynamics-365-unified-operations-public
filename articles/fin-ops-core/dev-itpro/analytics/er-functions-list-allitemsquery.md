---
# required metadata

title: ALLITEMSQUERY ER function
description: This topic provides information about how the ALLITEMSQUERY ER function is used.
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

# <a name="COLLECTEDLIST">COLLECTEDLIST Function</a>

[!include [banner](../includes/banner.md)]

# <a name="ALLITEMSQUERY">ALLITEMSQUERY Function</a>

The `ALLITEMSQUERY` function runs as a joined SQL query and returns a new flattened *Record list* as a list of records that represent all items that match the specified path.

## Syntax

```
ALLITEMSQUERY (path)
```

## Arguments

`path` : *Record list*

A valid path to a data source of the *Record list* data type. It must contain at least one relation.

## Returns

*Record list*

The result list of records.

## Usage notes

The specified path must be defined as a valid data source path of a data source element of the *Record list* data type. It must also contain at least one relation. Data elements such as the path *String* and *Date* should raise an error in the ER
expression builder at design time.

When this function is applied to a data sources of the *Record list* data type that refer to an application object that can be directly called by using SQL (table, entity, query), it runs as a joined SQL query. Otherwise, it is executed
in memory as the [ALLITEMS](er-functions-list-allitems.md) function.

## Example

Define the following data sources in your model mapping:

-   **CustInv** (`Table records` type), which refers to the
    **CustInvoiceTable** table.

-   **FilteredInv** (`Calculated field` type), which contains the expression** `FILTER (CustInv, CustInv.InvoiceAccount = "US-001")`

-   **JourLines** (`Calculated field` type), which contains the
    expression `ALLITEMSQUERY ( FilteredInv.'<Relations'.CustInvoiceJour.'<Relations'.CustInvoiceTrans)`

When you run your model mapping to call the **JourLines** data source, the following SQL statement is executed:

`SELECT ... FROM CUSTINVOICETABLE T1 CROSS JOIN CUSTINVOICEJOUR T2 CROSS JOIN
CUSTINVOICETRANS T3 WHERE...`


## Additional resources

[List functions](er-functions-category-list.md)
