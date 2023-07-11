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

Starting in Dynamics 365 Finance version 10.0.35, the functionality for [VAT exchange rate](emea-vat-exchange-rate.md) is extended for more countries/regions.

In addition to the country/region extension, the following capabilities were enhanced:
 - Support of direct recalculation from transaction currency to the tax currency
 - Support of amounts adjustment in the tax currency.

## Prerequisites and setup

This functionality is available only for legal entities who have enabled the Tax calculation service (TCS) for the selected business processes. To learn about TCS, its capabilities, and how to set it up, refer to the [Tax Calculation overview](global-tax-calcuation-service-overview.md) article.

In addition, enable the following features in the **Feature management** workspace:

 - Date of VAT register [Tax point date (Date of VAT register)](emea-tax-point-date.md).
 - Enable exchange rate types for sales tax

After you enable the features, you might need to refresh the page to update the UI. 

> [!NOTE]
> If you haven’t used the Date of VAT register functionality,  follow the instructions described in the article, [Sales tax transactions extension consistency check](emea-tax-point-date.md#sales-tax-transactions-extension-consistency-check).

On the **General ledger parameters** page, on the **Sales tax** tab, on the **Tax options** FastTab, set **Enable exchange rate types for sales tax** to **Yes**.
We recommend you enable this parameter in a new tax settlement period. Make sure to run the **Settle and post sales tax** periodic procedure for the current tax settlement period.

After you enable the functionality, you will receive the message, "By enabling this parameter, you are changing the tax calculation method for operations in foreign currency. Tax amounts will be converted directly from the transaction currency to the tax currency using the exchange rates set for the exchange rate types for sales tax. And the “Sales tax conversion” option will be disabled. Because this option controls how to convert tax amount from transaction currency to tax currency - via either Accounting currency or Reporting currency."

![Enable exchange rate type dialog box.](media/GLParamenters_EnableExchangeRateType_1.JPG)


Make sure that you run the **Recalculate tax** tasks located on the **Sales tax codes** page in the **Recalculate tax** group. Those tasks can include:

 - **Unposted transactions that use the selected taxes**
 - **All unposted transactions**

This procedure helps you update exchange rates for the calculated tax amounts for created but not posted sales tax transactions.

![Action required dialog box.](media/GLParamenters_EnableExchangeRateType_2.JPG)

Select exchange rate types in the **Sales tax receivable exchange rate type** and **Sales tax payable exchange rate type**, that will be used for purchase and sales operations. If the fields remain blank, the exchange rate will be taken from the exchange rate type set on the **Ledger** page.

![General ledger parameters and the Exchange rate types field group.](media/GLParamenters_EnableExchangeRateType_3.JPG)

Set up sales tax receivable and sales tax payable difference and difference offset accounts in the ledger posting groups at **Tax** > **Setup** > **Sales tax** > **Ledger posting groups**.

![Ledger posting groups.](media/PostingAccountsSalesTaxTaxExchRate_3-1.PNG)

## Overview

After you configure the parameters, you can post invoices that use foreign currency and adjust the exchange rate and tax amounts on the sales tax transactions page. 

On the **Sales Tax transactions page** of the document being processed, use the **Date of VAT register** field to select the date on which exchange rate for tax amounts calculations should be applied.
The **Sales tax exchange rate** and **Date of VAT register** fields are available for editing. 

You can also use the **Adjusted amount origin (VAT exchange rate)** or **Adjusted sales tax amount (VAT exchange rate)** field to enter actual VAT amounts in the local currency that is stated in an external document. When you review the accounting, you can view sales tax difference amounts on the **Subledger journal** page. 
This is relevant for the documents that follow the source document framework.

When a document is posted, for transactions that are posted to the general ledger accounts that you've configured, you can view any differences in sales tax amounts that are caused by the difference between the tax currency exchange rate and the accounting currency exchange rate for your organization.
For _Sales tax payable_ sales tax direction, the tax difference is posted with a _Sales tax payable difference tax direction_. For _Sales tax receivable_, tax adjustment will be recorded with _Sales tax receivable difference_ tax direction; for _use tax_, tax difference is posted with _Use tax_ sales tax direction.

> [!NOTE]
> In Finance version 10.0.35, adjustments for sales and purchase tax exempt transactions aren't supported.
> 
> After tax transactions are posted, updating the **Date of VAT register** in the **VAT register transactions** won’t affect to the tax adjustment transaction posting.

### Example

The following is a scenario with a legal entity who issues an invoice in a foreign currency. For example, a Free text invoice 1100 USD, including VAT 10%. The VAT must be calculated based on the special exchange rate.
       
| Currency  | Curency code |
|-----------|--------------|
| Legal entity accounting currency | EUR |
| Legal entity reporting currency | USD |
| Tax code currency | PLN |
| Transaction currency | USD |


Exchange rates for business accounting purposes, set up in the **Ledger**:

| Currency code |Exchange rate |
|---|---|
|USD : EUR| 1 : 0.92 |
|EUR : PLN| 1 : 4.44 |
|USD : PLN| 1 : 4.07 |

Exchange rates for tax calculation purposes, set up on the **Sales tax** tab on the **General ledger parameters** page:

| Currency code |Exchange rate |
|---|---|
|USD : EUR| 1 : 0.93 |
|EUR : PLN| 1 : 4.46 |
|USD : PLN| 1 : 4.06 |

Review the calculated sales tax, and in the Free text invoice, select **Sales tax** as shown in the following graphic.

![Sales tax transactions page Amount tab.](media/SalesTaxTransactionsTaxExchRate_4.PNG)

On the **Temporary sales tax transactions** page, you can review the exchange rates, amount origin, and tax amounts in the accounting currency, reporting currency, and tax currency. These amounts are shown for both exchange rate types, the one that is set in the **Ledger** and the one set in the **General ledger parameters**.

On the **Adjustment** tab, you can adjust tax amounts in the accounting currency and in the tax currency.

> [!NOTE]
> In this example, the reporting currency and transaction currency are the same (USD). This means the exchange rate for the reporting currency isn't editable.

On the **Subledger journal** page you can view amounts and accounts for the calculated sales tax difference. In this example, the exchange rate of currencies pair EUR-USD is different for the **Accounting currency exchange rate type** in the **Ledger** and **Sales tax payable exchange rate type** in the **General ledger parameters**.

![Sales tax transactions.](media/SalesTaxTransactionsTaxExchRate_4-1.PNG)

![SalesTaxTransactionsTaxExchRateSubledger.](media/SalesTaxTransactionsTaxExchRateSubledger_4-2.PNG)

After the document is posted, review the the posted sales tax transactions and voucher. The tax difference is posted with a **Sales tax payable difference** tax direction. 

![PostedSalesTaxTaxExchRate.](media/PostedSalesTaxTaxExchRate_5-1.PNG)

![PVoucherTaxExchRate.](media/VoucherTaxExchRate_5-1.PNG)

For example purposes, to demo the postings, all the ledger accounts are different. 

To reflect the tax difference on the sales tax payable and sales tax receivable tax accounts, you can select them in the **Sales tax payable difference** and  **Sales tax receivable difference**, respectively.

> [!NOTE]
> If the tax currency differs from the accounting and reporting currency, the tax difference amounts in tax currency are recorded in sales tax transaction only.
> 
> In the voucher, the tax difference is recorded in the accounting and reporting currency on ledger accounts that are set in the sales tax code posting.




