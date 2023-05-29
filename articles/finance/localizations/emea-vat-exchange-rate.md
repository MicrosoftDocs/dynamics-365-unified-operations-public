---
title: VAT exchange rate overview
description: This article provides information about exchange rates for the VAT calculation that's available for the Czech Republic, Hungary, and Poland.
author: mrolecki
ms.date: 07/08/2021
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Czech Republic, Hungary, Poland
ms.author: mrolecki
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 272703
ms.collection: get-started
ms.assetid: 2d1fad67-8234-49cc-b009-0f3cc29f5886
ms.search.form: ExchangeRateCurrencyPairCalculationRules, LedgerParameters, SalesTaxExchangeRateType, TaxTmpWorkTrans
---

# VAT exchange rate overview

[!include [banner](../includes/banner.md)]

This article provides information about exchange rates for the VAT calculation that's available for the Czech Republic, Hungary, and Poland. The exchange rate that's used for VAT calculation can differ from the exchange rate used for company accounting functions. When a document in a foreign currency is posted, any exchange rate differences that occur are posted to specific ledger accounts.

Your organization can select the exchange rate that it uses to calculate value-added tax (VAT) for VAT statements. This exchange rate can differ from the exchange rate that your organization uses for company accounting functions. Accounting functions include the preparation of the following tax-related documents:

-   Invoices
-   Free text invoices
-   Purchase orders
-   Project invoices
-   Credit notes
-   Corrective invoices

When you post a document that uses a foreign currency, any exchange rate differences that occur are posted to specific ledger accounts.

## Prerequisites

Before you can use this functionality, you must configure the system.

1.  Create exchange rate types and set up exchange rates for the sales tax at **General ledger** &gt; **Currencies** &gt; **Exchange rate types**. You can define as many exchange rate types and as many exchange rates for pairs of currencies as you require.
2.  Enable the calculation of VAT exchange rates by turning on the **Bank exchange rate** parameter, and by defining sales tax receivable and sales tax payable exchange rate types, at **General ledger** &gt; **Ledger setup** &gt; **General ledger parameters**.
3.  Set up currency exchange rate types for specific sales and purchase transaction types at **General ledger** &gt; **Currencies** &gt; **Currency exchange rate types for sales tax**.
4.  Set up sales tax receivable and sales tax payable difference and difference offset accounts in the ledger posting groups at **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Ledger posting groups**.
5.  Optional: Set up an exchange rate calculation rule for a currency pair at **General ledger** &gt; **Currencies** &gt; **Exchange rate calculation rules for currency pairs**. The exchange rate calculation rules are used to convert VAT amounts for foreign currency sales invoices to VAT amounts in a destination currency.

## Overview

After you've configured the system to use VAT exchange rates, if you must enter a document or create an order that uses a foreign currency, you can use **Sales tax transactions** page to set the **Date of VAT register** value to pick up and set the default **Sales tax exchange rate** value. You can edit both fields. You can also use the **Adjusted amount origin (VAT exchange rate)** or **Adjusted sales tax amount (VAT exchange rate)** field to enter actual VAT amounts in the local currency that is stated in an external document. When you review the accounting, you can view sales tax difference amounts on the **Subledger journal** page. When a document is posted, for transactions that are posted to the general ledger accounts that you've configured, you can view any differences in sales tax amounts that are caused by the difference between the VAT currency exchange rate and the accounting currency exchange rate for your organization.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
