---
title: Exchange rate type for sales tax
description: This article explains the logic for calculation of sales tax on the special exchange rate.
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
ms.dyn365.ops.version: AX 10.0.36
---

# Exchange rate type for sales tax

[!include [banner](../includes/banner.md)]

This article explains the logic for exchange rate type setup and calculation for sales tax.

Starting from the 10.0.35 version, the functionality for [VAT exchange rate](emea-vat-exchange-rate.md) is extended for more countries/regions.

In addition, the following capabilities were enhanced:
 - Support of direct recalculation from transaction currency to tax currency.
 - Support of amounts adjustment in Tax currency.


## Prerequisites and setup

This functionality is available only for the legal entities with the enabled Tax calculation service (TCS) for the selected business processes. To learn about TCS, its capabilities and how to set it up, please refer to the [Tax Calculation overview] (global-tax-calcuation-service-overview.md).

In addition, enable the following features in the **Feature management** workspace:

•	Date of VAT register [Tax point date (Date of VAT register)](emea-tax-point-date.md).
•	Enable exchange rate types for sales tax

After enabling features, you might need to refresh the page to get the UI updated. 

> [!NOTE]
> If you haven’t used the Date of VAT register functionality, make sure you follow instructions described in the [Sales tax transactions extension consistency check](emea-tax-point-date.md#sales-tax-transactions-extension-consistency-check).
>

In the **General ledger parameters**, on **Sales tax** tab, **Tax options** FastTab, set the **Enable exchange rate types for sales tax** to **Yes**.
It is recommended to enable this parameter in a new tax settlement period. Make sure you ran the **Settle and post sales tax** periodic procedure for the current tax settlement period.

Once the functionality is enabled, you will receive a message: "By enabling this parameter, you are changing the tax calculation method for operations in foreign currency. Tax amounts will be converted directly from the transaction currency to the tax currency using the exchange rates set for the exchange rate types for sales tax. And the “Sales tax conversion” option will be disabled. Because this option controls how to convert tax amount from transaction currency to tax currency - via either Accounting currency or Reporting currency."

Also, make sure that you run the “Recalculate tax” task(s) located on the “Sales tax codes” page under the “Recalculate tax” group: “Unposted transactions that use the selected taxes” and/or “All unposted transactions”. This procedure will help to update exchange rates for the calculated tax amounts for already created but not posted sales tax transactions.

Select exchange rate types in the **Sales tax receivable exchange rate type** and **Sales tax payable exchange rate type**, that will be used for purchase and sales operations. If the fields remain blank, the exchange rate will be taken from the exchange rate type set on the **Ledger** page.

SCREENSHOT

Set up sales tax receivable and sales tax payable difference and difference offset accounts in the ledger posting groups at **Tax** > **Setup** > **Sales tax** > **Ledger posting groups**.

SCREENSHOT

## Overview

Once all the parameters are configured, you can post invoices that use foreign currency and adjust exchange rate and/or tax amounts on the sales tax transactions page. 

On the **Sales Tax transactions page** of the document being processed, you can use the **Date of VAT register** field to select the date on which exchange rate for tax amounts calculations should be applied.
Both **Sales tax exchange rate** and **Date of VAT register** fields are available for editing. 

You can also use the **Adjusted amount origin (VAT exchange rate)** or **Adjusted sales tax amount (VAT exchange rate)** field to enter actual VAT amounts in the local currency that is stated in an external document. When you review the accounting, you can view sales tax difference amounts on the **Subledger journal** page. 
This is relevant for the documents that follow the source document framework.

When a document is posted, for transactions that are posted to the general ledger accounts that you've configured, you can view any differences in sales tax amounts that are caused by the difference between the tax currency exchange rate and the accounting currency exchange rate for your organization.
For _Sales tax payable_ sales tax direction, the tax difference is posted with a _Sales tax payable difference tax direction_. For _Sales tax receivable_, tax adjustment will be recorded with _Sales tax receivable difference_ tax direction; for _use tax_, tax difference is posted with _Use tax_ sales tax direction.

> [!NOTE]
> In 10.0.35, adjustments for sales and purchase tax exempt transactions are not supported.
> 
> After tax transactions are posted, updating the **Date of VAT register** in the **VAT register transactions** won’t affect to the tax adjustment transaction posting.
> 

### Example

Let’s review the scenario when a legal entity issues an invoice in a foreign currency (e.g., a Free text invoice 1100 USD, incl. VAT 10%), and you need to calculate VAT based on the special exchange rate.
       
   | Currency  |Curency code |
|---|---|
| Legal entity accounting currency | EUR |
| Legal entity reporting currency | USD |
| Tax code currency | PLN |
| Transaction currency | USD |


Exchange rates for business accounting purposes, set up in the **Ledger**:

| Currency code |Exchange rate |
|---|---|
|EUR : USD| 1 : 1.09 |
|EUR : PLN| 1 : 4.44 |
|USD : PLN| 1 : 4.07 |

Exchange rates for tax calculation purposes, set up in the **General ledger parameters**, **Sales tax** tab:

| Currency code |Exchange rate |
|---|---|
|EUR : USD| 1 : 1.09 |
|EUR : PLN| 1 : 4.46 |
|USD : PLN| 1 : 4.06 |

Review the calculated sales tax, click **Sales tax button** in **Free text invoice**:

Screenshot

In the **Temporary sales tax transactions**, you can review the exchange rates, amount origin and tax amounts in accounting currency, reporting currency and tax currency. These amounts are shown for both exchange rate types, the one that is set in the **Ledger** and the one set in the **General ledger parameters**.

SCREENSHOT

On the **Adjustment** tab you can adjust tax amounts in accounting currency and in tax currency.

> [!NOTE]
> In our example the reporting currency and transaction currency are the same (USD), thus the exchange rate for the reporting currency is not editable.
> 

On the **Subledger journal** page you can view amounts and accounts for the calculated sales tax difference. In our example, the exchange rate of currencies pair EUR-USD is different for the Accounting currency exchange rate type in the **Ledger** and **Sales tax payable exchange rate type** in the **General ledger parameters**.

SCREENSHOTs with tax trans and subledger

After document is posted, you can review the voucher and posted sales tax transactions. The tax difference is posted with a **Sales tax payable difference** tax direction. 

> [!NOTE]
> For this example purposes, to demo the postings, all the ledger accounts are different.
> 
> To reflect the tax difference on the sales tax payable and sales tax receivable tax accounts, you can pick them in the Sales tax payable difference and  Sales tax receivable difference, respectively.
> 

> [!NOTE]
> In case tax currency differs from accounting and reporting currency, the tax difference amounts in tax currency are recorded in sales tax transaction only.
> 
> In voucher, the tax difference is recorded in accounting and reporting currency on ledger accounts that are set in sales tax code posting.
> 




