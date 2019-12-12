---
# required metadata

title: FILTER ER function
description: This topic provides information about how the FILTER ER function is used.
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

# <a name="FILTER">FILTER Function</a>

[!include [banner](../includes/banner.md)]

The `FILTER` function returns the specified list as a *Record list* after the query has been modified to filter for a given condition.

## Syntax

```
FILTER (list, condition)
```

## Arguments

`list` : *Record list*

A valid path to a data source of the *Record list* data type.

`condition` : *Boolean*

A valid conditional expression to filter records of a given list.

## Returns

*Record list*

The result list of records.

## Usage notes

This function differs from the [WHERE](er-functions-list-where.md) function, because the specified condition is applied to any ER data source of the *Table
records* type at the database level. The list and condition can be defined by using tables and relations.

When the configured arguments of this functions (list or condition or both) do not allow to translate this request to the direct SQL call, an exception is thrown at design time informing that either list or condition is not usable for
querying database.

## Example 1

If **Vendor** is configured as an ER data source that refers to the **VendTable** table, the `FILTER (Vendors, Vendors.VendGroup = "40")` expression returns a list of only the vendors that belong to vendor group **40**.

## Example 2

If **Vendor** is configured as an ER data source that refers to the **VendTable** table, and if **parmVendorBankGroup** is configured as an ER data source that returns a value of the `String` data type, the `FILTER ( Vendor.'<Relations'.VendBankAccount, 
Vendor.'<Relations'.VendBankAccount.BankGroupID = parmVendorBankGroup)` expression returns a list of only the vendor accounts that belong to a specific bank group.

## Example 3

If you enter the data source **DS** of the `Calculated field` type and it contains the expression `SPLIT ("A,B,C", “,”)`, you can enter another expression `FILTER( DS, DS.Value = “B”)`. The exception “Validation error: The list expression of FILTER function is not queryable.” is thrown when you try to save this expression in the ER formula designer.

## Additional resources

[List functions](er-functions-category-list.md)
