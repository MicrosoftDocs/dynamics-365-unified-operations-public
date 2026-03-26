---
title: Tax reporting by reporting codes
description: Learn about general information about how to set up and generate the tax statement, including a tax statement overview.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/30/2025
ms.reviewer: johnmichalak

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

The tax statement is based on tax transaction amounts. The process of generating a tax statement is part of the **Sales tax payment** process, which is implemented through the **Settle and post sales tax** function. This function calculates the sales tax that's due for a given period. The settlement calculation includes the posted sales tax for the selected settlement period for the tax transactions. For more information, see [Create a sales tax payment](../../general-ledger/tasks/create-sales-tax-payment.md). The process for calculating data for a tax statement is based on the relationship between sales tax codes and sales tax reporting codes, where sales tax reporting codes match the tax statements boxes (or tags in XML). For each sales tax code, set up sales tax reporting codes for each type of transaction, such as taxable sales, taxable purchases, and taxable import. These types of transactions are described in the [Sales tax codes for tax reporting](#sales-tax-codes-for-tax-reporting) section later in this article.

For each sales tax reporting code, determine a specific report layout. At the same time, link sales tax codes to a specific sales tax authority through sales tax settlement periods. For every sales tax authority, determine a report layout. Thus, you can select only sales tax reporting codes with the same report layout that you set up for a sales tax authority in sales tax settlement periods for the sales tax code in the report setup of the sales tax code. A sales tax transaction generated upon posting an order or a journal contains a sales tax code, sales tax source, sales tax direction, and transaction amounts (tax base amount and tax amount in accounting currency, sales-tax currency, and transaction currency). Based on the combination of tax transaction attributes, transaction amounts compose total amounts for sales tax reporting codes specified for sales tax codes. The following illustration shows the data relationship.

:::image type="content" source="../media/diagram4.jpg" alt-text="Screenshot of diagram showing the data relationship for tax reporting.":::

## Tax statement setup

To generate a tax statement, set up the following items.

### Sales tax authorities for tax reporting

Before you can set up sales tax reporting codes, select the correct report layout for the sales tax authority. On the [Sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md) page, in the **General** section, select a report layout. Use this layout when you set up sales tax reporting codes.

<!---For general information about setting up a sales tax authority, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md). -->

### Sales tax reporting codes

Sales tax reporting codes are box codes in the tax statement or tag names in XML format. Use these codes to aggregate and prepare amounts for the report. When you configure the electronic reporting format of the tax statement, use the names of the result amounts. You can create and maintain sales tax reporting codes on the [Sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md) page. Assign each code a report layout. After you create the sales tax reporting codes, you can choose the codes in the **Report setup** section on the **Sales tax codes** page.

### Sales tax codes for tax reporting

You can aggregate base amounts and tax amounts of sales tax transactions on reporting codes in the tax statement (XML tags or declaration boxes). Set up this behavior by associating sales tax reporting codes for different transaction types with sales tax codes on the **Sales tax codes** page. The following table describes the transaction types in the report setup for sales tax codes. The calculation includes transactions for all types of sources except sales tax.<!--For general information about how to set up sales tax codes, see [Set up sales tax codes](../../general-ledger/tasks/set-up-sales-tax-codes.md).-->

| Transaction type | Description of transactions and amounts to be counted on the transaction type |
|---|---|
| Taxable Sales | Sum of **Tax base amounts** of tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The sale is domestic (**Tax direction** is **Sales tax payable**).<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Tax-free sales | Sum of **Tax base amounts** of tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The sale is export (**Tax direction** is **Tax-free sale**).<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Sales tax payable | Sum of **Tax amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The sale is domestic (**Tax direction** is **Sales tax payable**).<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Taxable sales credit note | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The sale is domestic (**Tax direction** is **Sales tax payable**).<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Fax exempt sales credit note | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The sale is export (**Tax direction** is **Tax-free sale**).<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Sales tax on sales credit note | Sum of **Tax amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The sale is domestic (**Tax direction** is **Sales tax payable**).<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Taxable purchases | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The purchase is domestic (**Tax direction** is **Sales tax receivable**).<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Tax-free purchase | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The purchase is import (**Tax direction** is **Tax-free purchase**).<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Sales tax receivable | Sum of **Tax amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The purchase is domestic (**Tax direction** is **Sales tax receivable**).<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Taxable purchase credit note | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The purchase is domestic (**Tax direction** is **Sales tax receivable**).<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Tax exempt purchase credit note | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The purchase is import (**Tax direction** is **Tax-free purchase**).<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Sales tax on purchase credit note | Sum of **Tax amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- The purchase is domestic (**Tax direction** is **Sales tax receivable**).<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Taxable import | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- **Tax direction** is **Use tax**.<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Offset taxable import | Reversed sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- **Tax direction** is **Use tax**.<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Taxable import credit note | Sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- **Tax direction** is **Use tax**.<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Offset taxable import credit note | Reversed sum of **Tax base amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- **Tax direction** is **Use tax**.<br>- The transaction **Tax base amount** or **Tax amount** is less than 0. |
| Use tax | Sum of **Tax amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- **Tax direction** is **Use tax**.<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |
| Offset use tax | Reversed sum of **Tax amounts** of the tax transactions that satisfy the following conditions:<br>- Transaction date is in the selected period.<br>- **Tax direction** is **Use tax**.<br>- The transaction **Tax base amount** or **Tax amount** is greater than 0. |

> [!NOTE]
> For the preceding table, the following criteria are met:
>
> - The tax base amount is a transaction amount from the **Origin in Accounting currency** field.
> - The tax amount is a transition amount from the **Actual sales tax amount in Accounting currency** field.

## Country/region-specific resources for tax statements

The tax statement for each country/region must meet the requirements of that country/region's legislation. There are predefined general models and formats of tax statements for the countries/regions that are listed in the following table.

| Country/region | Additional information |
|----------------|------------------------|
| Australia      | [Business activity statement (BAS)](../australia/apac-aus-business-activity-statement.md) |
| Japan          | [Japan consumption tax report](../japan/apac-jpn-consumption-tax-report.md) |
| Poland         | [VAT declaration with registers \(JPK-V7, VDEK\)](../poland/emea-pol-vdek.md) |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
