---
title: ORDERBY ER function
description: This article provides information about how the ORDERBY Electronic reporting (ER) function is used.
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

# ORDERBY ER function

[!include [banner](../includes/banner.md)]

The `ORDERBY` function returns the specified list as a *Record list* value after it has been sorted according to the specified arguments. These arguments can be defined as expressions.

## <a name="syntax-1"></a>Syntax 1

```vb
ORDERBY (list, expression 1[, expression 2, …, expression N])
```

## <a name="syntax-2"></a>Syntax 2

```vb
ORDERBY (location, list, expression 1[, expression 2, …, expression N])
```

> [!NOTE]
> This syntax is supported for Microsoft Dynamics 365 Finance version 10.0.25 and later.

## Arguments

`location`: *[String](er-formula-supported-data-types-primitive.md#string)*

The location where sorting should be run. The following options are valid:

- "Query"
- "InMemory"

`list`: *[Record list](er-formula-supported-data-types-composite.md#record-list)*

The valid path of a data source of the *Record list* data type.

`expression 1`: *Field*

The valid path of a field of the data source that is referenced by the `list` argument of the called function. The referenced field must be a field of the primitive data type. This argument is required.

`expression N`: *Field*

The valid path of a field of the data source that is referenced by the `list` argument of the called function. The referenced field must be a field of the primitive data type. These additional arguments are optional.

## Return values

*Record list*

The resulting list of records.

## Usage notes

### Syntax 1

Data sorting is always done in the memory of the application server. For more details, see [example 1](#example-1).

### Syntax 2

### Sorting in memory

When the `location` argument is specified as **InMemory**, data sorting is done in the memory of an application server. For more details, see [example 2](#example-2).

### Sorting in database

When the `location` argument is specified as **Query**, data sorting is done at the database level. In this case, the `list` argument must point to one of the following [Electronic reporting (ER)](general-electronic-reporting.md) data sources that specifies the application source that a direct database query can be established for:

- Data source of the *Table records* type
- Relation of a data source of the *Table records* type
- Data source of the *Calculation field* type

The `expression 1` and `expression N` arguments must point to fields of an ER data source that specifies the relevant fields of the application source that a direct database query can also be established for.

If a direct database query can't be established, a validation [error](er-components-inspections.md#i18) occurs in the ER model mapping designer. The message that you receive states that the ER expression that includes the `ORDERBY` function can't be run at runtime.

For better performance, we recommend that you use the **Query** option when the sorting is configured for application data sources that might contain the large number of records (for example, for transactional application tables).

> [!NOTE]
> The `ORDEBY` function itself can't be translated to a direct database query. Therefore, an ER data source that contains this function isn't queryable. It also can't be used in the scope of ER functions such as [FILTER](er-functions-list-filter.md) and [ALLITEMSQUERY](er-functions-list-allitemsquery.md), where only queryable data sources can be used.

For more details, see [example 3](#example-3) and [example 4](#example-4).

### Comparability

Because the SQL database engine and Finance application server can use a different ranking value for a single character, the sorting result of the same list of records can differ when a [String](er-formula-supported-data-types-primitive.md#string) field is used for sorting. For more details, see [example 5](#example-5).

## <a name="example-1"></a>Example 1: In-memory default execution

If you enter data source **DS** of the *Calculated field* type, and it contains the expression `SPLIT ("C|B|A", "|")`, the expression `FIRST( ORDERBY( DS, DS. Value)).Value` returns the text value **"A"**.

## <a name="example-2"></a>Example 2: In-memory explicit execution

If **Vendor** is configured as an ER data source of the *Table records* type that refers to the **VendTable** table, both the expression `ORDERBY (Vendor, Vendor.'name()')` and the expression `ORDERBY ("InMemory", Vendor, Vendor.'name()')` return a list of vendors that is sorted by name in ascending order.

When you configure the expression `ORDERBY ("Query", Vendor, Vendor.'name()')` in the ER model mapping designer, a validation [error](er-components-inspections.md#i8) occurs at design time, because the `Vendor.'name()'` path refers to an application method that has logic that can't be translated to a direct database query.

## <a name="example-3"></a>Example 3: Database query

If **TaxTransaction** is configured as an ER data source of the *Table records* type that refers to the **TaxTrans** table, the expression `ORDERBY ("Query", TaxTransaction, TaxTransaction.TaxCode)` sorts records at the application database level and returns a list of tax transactions that is sorted by tax code in ascending order.

## <a name="example-4"></a>Example 4: Queryable data sources

If **TaxTransaction** is configured as an ER data source of the *Table records* type that refers to the **TaxTrans** table, the **TaxTransactionFiltered** ER data source can be configured so that it contains the expression `FILTER(TaxTransaction, TaxCode="VAT19")` that will fetch transactions for a specified tax code. Because the configured **TaxTransactionFiltered** ER data source is queryable, the expression `ORDERBY ("Query", TaxTransactionFiltered, TaxTransactionFiltered.TransDate)` can be configured to return the list of filtered tax transactions that is sorted by transaction date in ascending order.

If you configure **TaxTransactionOrdered** as an ER data source of the *Calculated field* type that contains the expression `ORDERBY ("Query", TaxTransaction, TaxTransaction.TransDate)` and an ER data source of the *Calculated field* type that contains the expression `FILTER(TaxTransactionOrdered, TaxCode="VAT19")`, a validation [error](er-components-inspections.md#i18) occurs at design time in the ER model mapping designer. This error occurs because the first argument of the [FILTER](er-functions-list-filter.md#usage-notes) function must refer a queryable ER data source, but the **TaxTransactionOrdered** data source that contains the `ORDERBY` function isn't queryable.

## <a name="example-5"></a>Example 5: Comparability

### Prerequisites

1. Enter data source **DS1** of the *Calculated field* type that contains the expression `SPLIT ("D1|_D2|D3", "|")`.
2. Open the **[Financial dimension values](../../../finance/general-ledger/financial-dimensions.md)** page, and select the **CostCenter** dimension.
3. Enter the following dimension values: **D1**, **\_D2**, and **D3**.

### Sorting in memory

1. Configure data source **DS2** of the *Calculated field* type that contains the expression `ORDERBY("InMemory", DS1, DS1.Value)`.
2. Notice that the expression `FIRST(DS2).Value` returns the text value **"D1"**, the expression `INDEX(DS2, COUNT(DS2)).Value` returns the text value **"\_D2"**, and the expression `STRINGJOIN(DS2, DS2.Value, "|")` returns the text value **"D1\|D3\|\_D2"**.

### Sorting in database

1. Enter data source **DS3** of the *Table records* type that refers to the **FinancialDimensionValueEntity** entity.
2. Configure data source **DS4** of the *Calculated field* type that contains the expression `FILTER(DS3, DS3.FinancialDimension="CostCenter")`.
3. Configure data source **DS5** of the *Calculated field* type that contains the expression `ORDERBY(DS4, DS4.DimensionValue)`.
4. Notice that the expression `FIRST(DS5).Value` returns the text value **"\_D2"**, the expression `INDEX(DS5, COUNT(DS5)).Value` returns the text value **"D3"**, and the expression `STRINGJOIN(DS5, DS5.Value, "|")` returns the text value **"\_D2\|D1\|D3"**.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
