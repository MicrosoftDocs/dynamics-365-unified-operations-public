---
title: Exchange rate type for sales tax
description: This article explains the logic for calculating sales tax on the special exchange rate.
author: epodkolz
ms.date: 07/10/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: 
ms.author: epodkolzina
ms.search.validFrom: 
ms.dyn365.ops.version: AX 10.0.35
---

# Exchange rate type for sales tax

[!include [banner](../includes/banner.md)]

This article explains the logic for exchange rate type setup and calculation for sales tax.

As of Microsoft Dynamics 365 Finance version 10.0.35, the functionality for [value-added tax (VAT) exchange rates](emea-vat-exchange-rate.md) is extended for more countries and regions. In addition, the following capabilities are enhanced:

- Support for direct recalculation from the transaction currency to the tax currency
- Support for amount adjustments in the tax currency

## Prerequisites and setup

This functionality is available only for legal entities that have enabled Tax Calculation service for the selected business processes. For more information about Tax Calculation service, its capabilities, and how to set it up, see [Tax Calculation overview](global-tax-calcuation-service-overview.md).

In addition, you must enable the following features in the **Feature management** workspace:

- **Date of VAT register** (For more information about this feature, see [Tax point date (Date of VAT register)](emea-tax-point-date.md).)
- **Enable exchange rate types for sales tax**

After you enable these features, you might have to refresh the page to update the user interface (UI).

> [!NOTE]
> If you haven't used the **Date of VAT register** functionality, follow the instructions in [Sales tax transactions extension consistency check](emea-tax-point-date.md#sales-tax-transactions-extension-consistency-check).

Next, on the **General ledger parameters** page, on the **Sales tax** tab, on the **Tax options** FastTab, set the **Enable exchange rate types for sales tax** option to **Yes**. We recommend that you enable this parameter in a new tax settlement period. Be sure to run the **Settle and post sales tax** periodic procedure for the current tax settlement period.

When you enable the parameter, you receive the following message:

> By enabling this parameter, you are changing the tax calculation method for operations in foreign currency. Tax amounts will be converted directly from the transaction currency to the tax currency using the exchange rates set for the exchange rate types for sales tax. And the "Sales tax conversion" option will be disabled. Because this option controls how to convert tax amount from transaction currency to tax currency - via either Accounting currency or Reporting currency.

![Message box that appears when you enable exchange rate types for sales tax.](media/GLParamenters_EnableExchangeRateType_1.JPG)

Another message prompts you to run the **Recalculate tax** tasks in the **Recalculate tax** group on the **Sales tax codes** page. Those tasks can include the following two tasks:

- Unposted transactions that use the selected taxes
- All unposted transactions

These tasks help you update exchange rates for the calculated tax amounts for sales tax transactions that have been created but haven't been posted.

![Action required message box.](media/GLParamenters_EnableExchangeRateType_2.JPG)

Next, on the **General ledger parameters** page, on the **Sales tax** tab, on the **Tax options** FastTab, in the **Sales tax receivable exchange rate type** and **Sales tax payable exchange rate type** fields, select the exchange rate types to use for purchase and sales operations. If you leave these fields blank, the exchange rates are taken from the exchange rate types that are set on the **Ledger** page.

![Exchange rate type fields on the General ledger parameters page.](media/GLParamenters_EnableExchangeRateType_3.JPG)

Finally, on the **Ledger posting groups** page (**Tax** \> **Setup** \> **Sales tax** \> **Ledger posting groups**), set up sales tax receivable and sales tax payable difference and difference offset accounts in the ledger posting groups.

![Difference and different offset account fields on the Ledger posting groups page.](media/PostingAccountsSalesTaxTaxExchRate_3-1.PNG)

## Overview of the functionality

After you set up the functionality, you can post invoices that use foreign currency, and adjust the exchange rate and tax amounts on the **Sales tax transactions** page.

On the **Sales Tax transactions** page of the document that's being processed, in the **Date of VAT register** field, select the date when the exchange rate for tax amount calculations should be applied. The **Sales tax exchange rate** and **Date of VAT register** fields are available for editing.

You can also use the **Adjusted amount origin (VAT exchange rate)** or **Adjusted sales tax amount (VAT exchange rate)** field to enter actual VAT amounts in the local currency that's stated in an external document. When you review the accounting, you can view sales tax difference amounts on the **Subledger journal** page. This information is relevant to documents that follow the source document framework.

When a document is posted, for transactions that are posted to the general ledger accounts that you've configured, you can view any differences in sales tax amount that are caused by the difference between the tax currency exchange rate and the accounting currency exchange rate for your organization. For the *Sales tax payable* sales tax direction, the tax difference is posted with a *Sales tax payable difference* tax direction. For the *Sales tax receivable* sales tax direction, the tax adjustment will be recorded with a *Sales tax receivable difference* tax direction. For use tax, the tax difference is posted with a *Use tax* sales tax direction.

> [!NOTE]
> Finance version 10.0.35 doesn't support adjustments for tax-exempt sales and purchase transactions.
> 
> After tax transactions are posted, an update of the **Date of VAT register** field on the **VAT register transactions** has no effect on the tax adjustment transaction posting.

### Example

In this example, a legal entity issues a free text invoice in a foreign currency. The invoice amount is 1,100 US dollars (USD) and includes VAT at a rate of 10 percent. The VAT must be calculated based on the special exchange rate.

| Currency | Currency code |
|---|---|
| Legal entity accounting currency | EUR |
| Legal entity reporting currency | USD |
| Tax code currency | PLN |
| Transaction currency | USD |

The following exchange rates are set up for business accounting purposes on the **Ledger** page.

| Currency code | Exchange rate |
|---|---|
| USD : EUR | 1 : 0.92 |
| EUR : PLN | 1 : 4.44 |
| USD : PLN | 1 : 4.07 |

The following exchange rates are set up for tax calculation purposes on the **Sales tax** tab of the **General ledger parameters** page.

| Currency code | Exchange rate |
|---|---|
| USD : EUR | 1 : 0.93 |
| EUR : PLN | 1 : 4.46 |
| USD : PLN | 1 : 4.06 |

On the **Sales tax transactions** page, on the **Amount** tab, review the calculated sales tax. Then, in the free text invoice, select **Sales tax**.

![Amount tab on the Sales tax transactions page.](media/SalesTaxTransactionsTaxExchRate_4.PNG)

On the **Temporary sales tax transactions** page, you can review the exchange rates, amount origin, and tax amounts in the accounting currency, reporting currency, and tax currency. These amounts are shown for both exchange rate types: the one that's set on the **Ledger** page and the one that's set on the **General ledger parameters** page.

On the **Adjustment** tab, you can adjust tax amounts in the accounting currency and the tax currency.

> [!NOTE]
> In this example, the reporting currency and transaction currency are the same (USD). Therefore, the exchange rate for the reporting currency isn't editable.

On the **Subledger journal** page, you can review amounts and accounts for the calculated sales tax difference. In this example, the exchange rate of the EUR-USD currency pair differs for the accounting currency exchange rate type on the **Ledger** page and the sales tax payable exchange rate type on the **General ledger parameters** page.

![Sales tax transactions page.](media/SalesTaxTransactionsTaxExchRate_4-1.PNG)

![Subledger journal page.](media/SalesTaxTransactionsTaxExchRateSubledger_4-2.PNG)

After the document is posted, review the posted sales tax transactions and voucher. The tax difference is posted with a *Sales tax payable difference* tax direction.

![Posted sales tax page.](media/PostedSalesTaxTaxExchRate_5-1.PNG)

![Voucher.](media/VoucherTaxExchRate_5-1.PNG)

For this example, all the ledger accounts are different to demonstrate the postings.

To reflect the tax difference on the sales tax payable and sales tax receivable tax accounts, you can select them in the **Sales tax payable difference** and **Sales tax receivable difference** fields, respectively.

> [!NOTE]
> If the tax currency differs from the accounting and reporting currencies, the tax difference amounts in the tax currency are recorded only in the sales tax transaction.
> 
> In the voucher, the tax difference is recorded in the accounting and reporting currencies on ledger accounts that are set in the sales tax code posting.
