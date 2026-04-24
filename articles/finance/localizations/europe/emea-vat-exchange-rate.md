---
title: VAT exchange rate overview
description: Learn about exchange rates for the VAT calculation that's available for the Czech Republic, Hungary, and Poland, including prerequisites.
author: epodkolzina
ms.author: epodkolzina
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Czech Republic, Hungary, Poland
ms.search.validFrom: 2016-11-30
ms.search.form: ExchangeRateCurrencyPairCalculationRules, LedgerParameters, SalesTaxExchangeRateType, TaxTmpWorkTrans
ms.assetid: 2d1fad67-8234-49cc-b009-0f3cc29f5886
---

# VAT exchange rate overview

[!include [banner](../../includes/banner.md)]

This article provides information about exchange rates for the VAT calculation that's available for the Czech Republic, Hungary, and Poland. The exchange rate that you use for VAT calculation can differ from the exchange rate used for company accounting functions. When you post a document in a foreign currency, you post any exchange rate differences to specific ledger accounts.

Your organization can select the exchange rate that it uses to calculate value-added tax (VAT) for VAT statements. This exchange rate can differ from the exchange rate that your organization uses for company accounting functions. Accounting functions include the preparation of the following tax-related documents:

- Invoices
- Free text invoices
- Purchase orders
- Project invoices
- Credit notes
- Corrective invoices

When you post a document that uses a foreign currency, you post any exchange rate differences to specific ledger accounts.

## Prerequisites

Before you can use this functionality, you must configure the system.

1. Create exchange rate types and set up exchange rates for the sales tax at **General ledger** > **Currencies** > **Exchange rate types**. You can define as many exchange rate types and as many exchange rates for pairs of currencies as you require.
1. Enable the calculation of VAT exchange rates by turning on the **Bank exchange rate** parameter, and by defining sales tax receivable and sales tax payable exchange rate types, at **General ledger** > **Ledger setup** > **General ledger parameters**.
1. Set up currency exchange rate types for specific sales and purchase transaction types at **General ledger** > **Currencies** > **Currency exchange rate types for sales tax**.
1. Set up sales tax receivable and sales tax payable difference and difference offset accounts in the ledger posting groups at **Tax** > **Setup** > **Sales tax** > **Ledger posting groups**.
1. (Optional) Set up an exchange rate calculation rule for a currency pair at **General ledger** > **Currencies** > **Exchange rate calculation rules for currency pairs**. Use the exchange rate calculation rules to convert VAT amounts for foreign currency sales invoices to VAT amounts in a destination currency.

After you configure the system to use VAT exchange rates, if you must enter a document or create an order that uses a foreign currency, you can use **Sales tax transactions** page to set the **Date of VAT register** value to pick up and set the default **Sales tax exchange rate** value. You can edit both fields. You can also use the **Adjusted amount origin (VAT exchange rate)** or **Adjusted sales tax amount (VAT exchange rate)** field to enter actual VAT amounts in the local currency that is stated in an external document. When you review the accounting, you can view sales tax difference amounts on the **Subledger journal** page. When you post a document for transactions that post to the general ledger accounts that you configured, you can view any differences in sales tax amounts that are caused by the difference between the VAT currency exchange rate and the accounting currency exchange rate for your organization.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
