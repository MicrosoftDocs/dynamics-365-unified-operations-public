---
title: VALUEINLARGE ER function
description: This article provides information about how the VALUEINLARGE Electronic reporting (ER) function is used.
author: kfend
ms.date: 08/17/2020
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2020-08-01
ms.dyn365.ops.version: AX 10.0.14
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# VALUEINLARGE ER function

[!include [banner](../includes/banner.md)]

The `VALUEINLARGE` function determines whether the specified input of the *Int64* or *Integer* type matches any value of a specified item in the specified list. The function returns a *Boolean* value of **TRUE** if the specified input matches the result of running the specified expression for at least one record of the specified list. Otherwise, it returns a *Boolean* value of **FALSE**. To understand the difference with the `VALUEIN` function, see the [Usage note](#usage_note) section later in this article.

## Syntax

```vb
VALUEINLARGE (input, list, list item expression)
```

## Arguments

`input`: *Field*

The valid path of a data source item of the *Record list* type. The value of this item will be matched.

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

`list item expression`: *Expression*

A valid conditional expression that either points to or contains a single field of the specified list that should be used for the matching.

## Return values

*Boolean*

The resulting *Boolean* value.

## <a name="usage_note">Usage notes</a>

When the specified input represents an *Int64* or *Integer* type of a data source item, the call to which is translatable to a direct SQL statement, the specified list is converted to a temporary SQL table and matching is performed in the database by executing a single `EXISTS JOIN` query. Otherwise, this function works as the [`VALUEIN`](er-functions-logical-valuein.md) function.

When the specified input represents a data source item that is designed as an item other than *Int64* and *Integer* type, an error occurs at design time informing you that the `VALUEINLARGE` function is not applicable for the configured ER expression.

When the `VALUEINLARGE` function expression is executed and more than one temporary table is used in scope of this execution, a runtime error occurs.

## Example

You define the following data sources in your model mapping:

- The **In** data source of the *Table records* type.
    - This data source refers to the **Intrastat** table.
    - The **Cross-company** option is set to **No**.
- The **InMemory** data source of the *Calculated field* type.
    - This data source contains the expression `WHERE (In, In.Port <> "")`.
- The **InFiltered** data source of the *Calculated field* type.
    - This data source contains the expression `FILTER (In, VALUEINLARGE(In.RecId, InMemory, InMemory.RecId)`.

When the data source **InFiltered** is called under the context of the company **DEMF**, a new temporary table is created in the application database, the collected in memory list of record identification codes are inserted to this table, and the following SQL statement is generated to return filtered records of the **Intrastat** table.

```xpp
SELECT … from Intrastat T1
WHERE ((T1.PARTITION=?) AND (T1.DATAAREAID IN (N'DEMF'))) AND
EXISTS (SELECT 'x' FROM tempdb."DBO".? T2 WHERE ((T2.PARTITION=?) AND (T1.RecId=T2.RecId)))
```

## Additional resources

[Logical functions](er-functions-category-logical.md)

[VALUEIN functions](er-functions-logical-valuein.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
