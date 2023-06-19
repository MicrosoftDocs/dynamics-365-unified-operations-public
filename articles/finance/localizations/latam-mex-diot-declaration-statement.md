---
title: DIOT declaration statement
description: This article provides information about the DIOT declaration statement for Mexico.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Mexico
ms.author: atrukawk
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0cdb4da3-dca8-4e31-8fd5-8a1f785b5104
ms.search.form: DIOTDeclarationConcept_MX, DIOTDeclarationTaxCode_MX, VendTable
---

# DIOT declaration statement

[!include [banner](../includes/banner.md)]

This article provides information about the DIOT declaration statement for Mexico.

The DIOT declaration statement (informative declaration of operation with vendors) is used to report vendor transactions to the Mexican tax authorities (Servicio de Administración Tributaria \[SAT\]). You might have to do this if you're subject to value-added tax (VAT). The DIOT declaration statement is a text file. You can generate this file in Dynamics 365 Finance, and then import it into the government validation and delivery tool. Consolidated and detailed reports are also generated for control purposes. The statement includes transactions that were generated from purchase orders, invoice register journals, invoice approval journals, invoice journals. It also includes vendor transactions that were generated from the **Project** module. Additionally, you can include open transactions or settled transactions.

## Prerequisites
You must complete the following setup before you can generate the DIOT text file or related reports:

1.  Enter tax registration IDs or numbers for your legal entity.
2.  Enter tax information for vendors.

## Tax information for unmanaged vendors
Unmanaged vendors are vendors that don't have their details registered as vendor accounts in Finance. When a purchase transaction is registered for this type of vendor, you can select any ledger account other than the vendor account. Because all purchase transactions are included in the DIOT declaration statement, purchase transactions for unmanaged vendors also require tax registration IDs (RFC or CURP), the type of operation, and other additional information. For regular vendors, you can define additional information on the **Vendors** page. However, you can't do this for unmanaged vendors. To capture the required tax information for unmanaged vendors, you can enter additional information at the transaction level in the following journal transactions when the vendor account isn't identified:

-   Invoice journal
-   Invoice register
-   Expense journal

To define sales tax codes to make additional information fields available for an unmanaged vendor in journal transactions, you must specify a sales tax code that was set up to allow for additional information in the journal.

## DIOT report configuration
This section describes how to define the concepts and attach the sales tax codes that are required to generate the DIOT declaration statement. In Finance, a concept represents purchase transaction amounts that are grouped under different VAT percentages, as specified by the tax authorities in Mexico. In the DIOT text file, the total amounts are grouped for each vendor, based on the concepts that were previously defined. These concepts are reported in columns 8 through 22 of the DIOT layout format. The other columns of the report are automatically filled in based on vendor information such as the RFC, type of operation, and other related data.

### Example of concepts

| Concept ID | Concept description                               | Column position in the text file (Order number) |
|------------|---------------------------------------------------|-------------------------------------------------|
| 1          | The base amount of purchases at VAT 16% (settled) | 8                                               |
| 2          | The base amount of purchases at VAT 15% (settled) | 9                                               |
| 3          | VAT amount non recoverable at 16% or 15%          | 10                                              |

You can create new concepts on the **DIOT declaration** page. However, you can create only 15 concepts. The first concept should be order number 8 and the last should be order number 22. You can start to create the concepts in a different order, but you must complete all of them (8 through 22) to prevent inconsistencies in the government validation tool. For each concept, you must specify a column type. Specify a column type of **None** if the column has been deprecated. Some columns no longer apply and must be reported with a **0,00** amount. If the check box isn't selected, the DIOT declaration statement shows the complete net amount or the tax amount. Additionally, for each column, you can indicate the non-deductible percentage of the net amount or tax amount that is shown in the DIOT declaration statement.

#### Example

If the net amount or tax amount is 10000.00 pesos, and the percentage of the non-deductible amount is 30 percent, the report displays only 30 percent of 10,000.00 pesos, or 3,000.00 pesos. Use the **Sales tax code** button to attach one or more sales tax codes to a concept.

## Generate the DIOT declaration statement
To generate the DIOT declaration statement, click **Tax** &gt; **Declarations** &gt; **Sales tax** &gt; **Generate DIOT declaration**. You must specify or select the following information.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Unrealized settlement period</td>
<td>Select the unrealized settlement period. This is the period that is used in the configuration of sales tax codes for conditional taxes.</td>
</tr>
<tr class="even">
<td>Realized settlement period</td>
<td>Select the realized settlement period. This is the period that is used in the configuration of sales tax codes.</td>
</tr>
<tr class="odd">
<td>From date</td>
<td>Select the period.</td>
</tr>
<tr class="even">
<td>DIOT report type</td>
<td>Select either <strong>Consolidated</strong> or <strong>Detailed</strong>.</td>
</tr>
<tr class="odd">
<td>Include transactions</td>
<td>Select the available options:
<ul>
<li><strong>Unrealized</strong> – Include only the unrealized purchase transactions (transactions that were not settled and created in the period).</li>
<li><strong>Realized</strong> – Include only the realized purchase transactions (transaction that were settled in the period).</li>
<li>Both</li>
</ul></td>
</tr>
<tr class="even">
<td>Generate file</td>
<td>Select <strong>Yes</strong> to generate the text file.</td>
</tr>
<tr class="odd">
<td>Percentage of global vendor operations</td>
<td>Enter a percentage of the total vendor transaction amount, based on which the vendor is identified as a <strong>Global</strong> or <strong>Local</strong> vendor. However, on the <strong>Vendors</strong> page, on the <strong>Invoice and delivery</strong> FastTab, <strong>15:domestic/global vendor</strong> must be specified for the vendor in the <strong>Type of vendor</strong> field.</td>
</tr>
<tr class="even">
<td>Upper limit</td>
<td>Enter the upper threshold amount for the global vendor. For a global vendor, the total payment amount that must be declared is less than or equal to the value in this field. For a domestic vendor, the total payment amount that must be declared is more than the value in this field.</td>
</tr>
</tbody>
</table>

In the DIOT declaration statement, the amounts have either positive or negative signs, depending on the amount type that is entered for the purchase transaction. See the following table.

| Amount type in the purchase transaction      | Sign displayed in the DIOT |
|----------------------------------------------|----------------------------|
| Credit amount                                | Plus sign (+)              |
| Debit amount                                 | Minus sign (–)             |
| Credit amount with positive-sales tax amount | Plus sign (+)              |
| Credit amount with negative-sales tax amount | Minus sign (–)             |
| Debit amount with positive-sales tax amount  | Minus sign (–)             |
| Debit amount with negative-sales tax amount  | Plus sign (+)              |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
