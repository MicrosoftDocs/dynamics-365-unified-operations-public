---
title: Tax reporting by reporting codes
description: Learn about general information about how to set up and generate the tax statement, including a tax statement overview.
author: liza-golub
ms.author: egolub
ms.topic: article
ms.date: 03/24/2022
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Australia, Japan, Latvia, Lithuania
ms.search.validFrom: 2016-11-30
ms.search.form: TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
---

# Tax reporting by reporting codes

[!include [banner](../../includes/banner.md)]

This article describes the general approach for setting up and generating the tax statement by reporting codes for some countries/regions. This approach is common for users in legal entities in the following countries/regions:

- Australia
- Japan

## Tax statement overview

The tax statement is based on tax transaction amounts. The process of generating a tax statement is part of the **Sales tax payment** process, which is implemented through the **Settle and post sales tax** function. This function calculates the sales tax that's due for a given period. The settlement calculation includes the posted sales tax for the selected settlement period for the tax transactions. For more information, see [Create a sales tax payment](../../general-ledger/tasks/create-sales-tax-payment.md). The process for calculating data for a tax statement is based on the relationship between sales tax codes and sales tax reporting codes, where sales tax reporting codes match the tax statements boxes (or tags in XML). For each sales tax code, sales tax reporting codes should be set up for each type of transaction, such as taxable sales, taxable purchases, taxable import. These type of transactions are described in the [Sales tax codes for tax reporting](#sales-tax-codes-for-tax-reporting) section later in this article.

For each sales tax reporting code, a specific report layout should be determined. At the same time, sales tax codes are linked to a specific sales tax authority through sales tax settlement periods. For every sales tax authority, a report layout should be determined. Thus, only sales tax reporting codes with the same report layout that's set up for a sales tax authority in sales tax settlement periods for the sales tax code can be selected in the report setup of the sales tax code. A sales tax transaction generated upon posting an order or a journal, contains a sales tax code, sales tax source, sales tax direction, and transaction amounts (tax base amount and tax amount in accounting currency, sales-tax currency, and transaction currency). Based on the combination of tax transaction attributes, transaction amounts compose total amounts for sales tax reporting codes specified for sales tax codes. The following illustration shows the data relationship.

![Diagram that shows the data relationship.](../media/diagram4.jpg)

## Tax statement setup

To generate a tax statement you must set up the following items.

### Sales tax authorities for tax reporting

Before you can set up sales tax reporting codes, you must select the correct report layout for the sales tax authority. On the [Sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md) page, in the **General** section, select a report layout. This layout will be used when you set up sales tax reporting codes.

<!---For general information about setting up a sales tax authority, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md). -->

### Sales tax reporting codes

Sales tax reporting codes are box codes in the tax statement or tag names in XML format. These codes are used to aggregate and prepare amounts for the report. When you configure the electronic reporting format of the tax statement, the names of the result amounts will be used. You can create and maintain sales tax reporting codes on the [Sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md) page. You must assign each code a report layout. After you create the sales tax reporting codes, you can choose the codes in the **Report setup** section on the **Sales tax codes** page.

### Sales tax codes for tax reporting

Base amounts and tax amounts of sales tax transactions can be aggregated on reporting codes in the tax statement (XML tags or declaration boxes). You can set up this behavior by associating sales tax reporting codes for different transaction types for sales tax codes on the **Sales tax codes** page. The following table describes the transaction types in the report setup for sales tax codes. The calculation includes transactions for all types of sources except sales tax.<!--For general information about how to set up sales tax codes, see [Set up sales tax codes](../../general-ledger/tasks/set-up-sales-tax-codes.md).-->

<table>
<thead>
<tr>
<th>Transaction type</th>
<th>Description of transactions and amounts to be counted on the transaction type</th>
</tr>
</thead>
<tbody>
<tr>
<td>Taxable Sales</td>
<td><p>Sum of <strong>Tax base amounts</strong> of tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period/</li>
<li>The sale is domestic (<strong>Tax direction</strong> is <strong>Sales tax payable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Tax-free sales</td>
<td><p>Sum of <strong>Tax base amounts</strong> of tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The sale is export (<strong>Tax direction</strong> is <strong>Tax-free sale</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Sales tax payable</td>
<td><p>Sum of <strong>Tax amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The sale is domestic (<strong>Tax direction</strong> is <strong>Sales tax payable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Taxable sales credit note</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The sale is domestic (<strong>Tax direction</strong> is <strong>Sales tax payable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Fax exempt sales credit note</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The sale is export (<strong>Tax direction</strong> is <strong>Tax-free sale</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Sales tax on sales credit note</td>
<td><p>Sum of <strong>Tax amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The sale is domestic (<strong>Tax direction</strong> is <strong>Sales tax payable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Taxable purchases</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The purchase is domestic (<strong>Tax direction</strong> is <strong>Sales tax receivable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Tax-free purchase</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The purchase is import (<strong>Tax direction</strong> is <strong>Tax-free purchase</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Sales tax receivable</td>
<td><p>Sum of <strong>Tax amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The purchase is domestic (<strong>Tax direction</strong> is <strong>Sales tax receivable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Taxable purchase credit note</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The purchase is domestic (<strong>Tax direction</strong> is <strong>Sales tax receivable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Tax exempt purchase credit note</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The purchase is import (<strong>Tax direction</strong> is <strong>Tax-free purchase</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Sales tax on purchase credit note</td>
<td><p>Sum of <strong>Tax amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li>The purchase is domestic (<strong>Tax direction</strong> is <strong>Sales tax receivable</strong>).</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Taxable import</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li><strong>Tax direction</strong> is <strong>Use tax</strong></li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Offset taxable import</td>
<td><p>Reversed sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li><strong>Tax direction</strong> is <strong>Use tax</strong>.</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Taxable import credit note</td>
<td><p>Sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li><strong>Tax direction</strong> is <strong>Use tax</strong>.</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Offset taxable import credit note</td>
<td><p>Reversed sum of <strong>Tax base amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li><strong>Tax direction</strong> is <strong>Use tax</strong>.</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &lt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Use tax</td>
<td><p>Sum of <strong>Tax amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li><strong>Tax direction</strong> is <strong>Use tax</strong>.</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
<tr>
<td>Offset use tax</td>
<td><p>Reversed sum of <strong>Tax amounts</strong> of the tax transactions which satisfy the following conditions:</p>
<ul>
<li>Transaction date is in the selected period.</li>
<li><strong>Tax direction</strong> is <strong>Use tax</strong>.</li>
<li>The transaction <strong>Tax base amount</strong> or <strong>Tax amount</strong> &gt; 0.</li>
</ul></td>
</tr>
</tbody>
</table>

> [!NOTE]
> For the preceding table, it's assumed that the following criteria are met:
>
> - The tax base amount is a transaction amount from the **Origin in Accounting currency** field.
> - The tax amount is a transition amount from the **Actual sales tax amount in Accounting currency** field.

## Country/region-specific resources for tax statements

The tax statement for each country/region must meet the requirements of that country/region's legislation. There are predefined general models and formats of tax statements for the countries/regions that are listed in the following table.

| Country/region | Additional information |
|----------------|------------------------|
| Australia      | [Business activity statement (BAS)](../australia/apac-aus-business-activity-statement.md) |
| Japan          | [Japan consumption tax report](../japan/apac-jpn-consumption-tax-report.md) |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
