---
title: ALLITEMSQUERY ER function
description: This article provides information about how the ALLITEMSQUERY Electronic reporting (ER) function is used.
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

# ALLITEMSQUERY ER function

[!include [banner](../includes/banner.md)]

The `ALLITEMSQUERY` function runs as a joined SQL query. It returns a new flattened *Record list* value that consists of a list of records that represent all items that match the specified path.

## Syntax

```vb
ALLITEMSQUERY (path)
```

## Arguments

`path`: *Record list*

The valid path of a data source of the *Record list* data type. It must contain at least one relation.

## Return values

*Record list*

The resulting list of records.

## Usage notes

The specified path must be defined as a valid data source path of a data source element of the *Record list* data type. It must also contain at least one relation. Data elements such as the path *String* and *Date* should raise an error in the Electronic reporting (ER) expression builder at design time.

When this function is applied to data sources of the *Record list* data type that refer to an application object that can be directly called by using SQL (for example, an table, entity, or query), it runs as a joined SQL query. Otherwise, it runs in memory as the [ALLITEMS](er-functions-list-allitems.md) function.

## Example

You define the following data sources in your model mapping:

- A **CustInv** data source of the *Table records* type that refers to the CustInvoiceTable table
- A **FilteredInv** data source of the *Calculated field* type that contains the expression `FILTER (CustInv, CustInv.InvoiceAccount = "US-001")`
- A **JourLines** of the *Calculated field* type that contains the expression `ALLITEMSQUERY ( FilteredInv.'<Relations'.CustInvoiceJour.'<Relations'.CustInvoiceTrans)`

When you run the model mapping to call the **JourLines** data source, the following SQL statement is run:

```sql
SELECT ... FROM CUSTINVOICETABLE T1 CROSS JOIN CUSTINVOICEJOUR T2 CROSS JOIN
CUSTINVOICETRANS T3 WHERE...
```

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
