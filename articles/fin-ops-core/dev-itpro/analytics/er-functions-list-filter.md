---
title: FILTER ER function
description: This article provides information about how the FILTER Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/14/2021
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

# FILTER ER function

[!include [banner](../includes/banner.md)]

The `FILTER` function returns the specified list as a *Record list* value after the query has been changed so that it filters for the specified condition.

## Syntax

```vb
FILTER (list, condition)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

`condition`: *Boolean*

A valid conditional expression that is used to filter records of the specified list.

## Return values

*Record list*

The resulting list of records.

## <a name="usage-notes"></a>Usage notes

This function differs from the [WHERE](er-functions-list-where.md) function, because the specified condition is applied to any Electronic reporting (ER) data source of the *Table records* type at the database level. The list and condition can be defined by using tables and relations.

If one or both arguments that are configured for this function (`list` and `condition`) don't allow this request to be translated to the direct SQL call, an exception is thrown at design time. This exception informs the user that either `list` or `condition` can't be used to query the database.

> [!NOTE]
> The `FILTER` function behaves differently than the `WHERE` function when the [`VALUEIN`](er-functions-logical-valuein.md) function is used to specify the selection criteria.
> 
> - If the `VALUEIN` function is used in scope of the `WHERE` function, and the second argument of `VALUEIN` refers to a data source that returns no records, the Boolean *[False](er-formula-supported-data-types-primitive.md#boolean)* value that `VALUEIN` returns is considered. Therefore, the expression `WHERE(Vendors, VALUEIN(Vendors.VendGroup, VendGroups, VendGroups.VendGroup))` returns no vendor records if the **VendGroups** data source returns no vendor group records.
> - If the `VALUEIN` function is used in scope of the `FILTER` function, and the second argument of `VALUEIN` refers to a data source that returns no records, the Boolean *[False](er-formula-supported-data-types-primitive.md#boolean)* value that `VALUEIN` returns is ignored. Therefore, the expression `FILTER(Vendors, VALUEIN(Vendors.VendGroup, VendGroups, VendGroups.VendGroup))` returns all vendor records of the **Vendors** data source, even if the **VendGroups** data source returns no vendor group records.

## Example 1

If **Vendor** is configured as an ER data source that refers to the VendTable table, the expression `FILTER (Vendors, Vendors.VendGroup = "40")` returns a list of only vendors that belong to vendor group 40.

## Example 2

If **Vendor** is configured as an ER data source that refers to the VendTable table, and if **parmVendorBankGroup** is configured as an ER data source that returns a value of the *String* data type, the expression `FILTER ( Vendor.'<Relations'.VendBankAccount, Vendor.'<Relations'.VendBankAccount.BankGroupID = parmVendorBankGroup)` returns a list of only vendor accounts that belong to a specific bank group.

## Example 3

You enter data source **DS** of the *Calculated field* type, and it contains the expression `SPLIT ("A,B,C", ",")`. You then enter another expression, `FILTER( DS, DS.Value = "B")`. When you try to save this expression in the ER formula designer, the following exception is thrown: "Validation error: The list expression of FILTER function is not queryable."

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
