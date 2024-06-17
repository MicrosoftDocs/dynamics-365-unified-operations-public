---
title: LISTDISTINCT ER function
description: Learn about how the LISTDISTINCT Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 07/30/2020
ms.custom: 
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-08-01
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 10.0.14
ms.assetid: 
---

# LISTDISTINCT ER Function

[!include [banner](../includes/banner.md)]

The `LISTDISTINCT` function calculates the specified expression as a selector for every record of the specified list. It returns a new *Record list* value that contains a single record for each unique selector value.

## Syntax

```
LISTDISTINCT (list, selector)
```

## Arguments

`list`: *Record list*

The valid path of a data source of the *Record list* data type.

`selector`: *Primitive data type*

A valid expression that is used to calculate a selector value for every record in the specified list.

The following data types are supported for this parameter:

- Boolean
- Date
- DateTime
- GUID
- Integer
- Int64
- Real
- String

## Return values

*Record list*

The resulting list of records.

## Usage notes

The structure of the list that is created matches the structure of the specified list.

The same selector value might be calculated for multiple records in the specified list. In this case, field values of the corresponding record in the created list equal the values of the first record from the specified list that the selector value is calculated for.

The execution of this function is done on any [Electronic reporting (ER)](general-electronic-reporting.md) data source of the *Record list* type that is present in memory.

The **GROUPBY** data source can also be used to generate the list of records that the selector that has distinct values is calculated for. However, from a performance and memory consumption perspective, it's better to use the `LISTDISTINCT` function than the **GROUPBY** data source, because the execution of the function is done in memory.

## Example

The following example shows how you can get the list of unique customer account numbers that at least one sales invoice or project invoice has been issued to during a specific period.

1. Enter the **SalesInvoice** data source of the `Record list` type that refers to the **CustInvoiceJour** application table and filters sales invoices for specific periods.

    The `InvoiceAccount` field of this data source returns the account number of an invoiced customer.

2. Enter the **ProjectInvoice** data source of the `Record list` type that refers to the **ProjInvoiceJour** application table and filters project invoices for specific periods.

    The `InvoiceAccount` field of this data source returns the account number of an invoiced customer.

3. Configure the **AllInvoices** data source of the `Calculated field` type that contains the expression `LISTJOIN(SalesInvoice, ProjectInvoice)`.

    This data source returns the joined list of sales invoices and project invoices.

4. Configure the **InvoicedCustomer** data source of the `Record list` type that contains the expression `LISTDISTINCT(AllInvoices, AllInvoices.InvoiceAccount)`.

    This data source returns a new list that contains a single record for every unique customer that has been invoiced during the defined period. The `InvoiceAccount` field of this list contains a customer account number.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
