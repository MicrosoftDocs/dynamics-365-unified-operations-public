---
title: Split the realized exchange difference amount into the difference of the invoice net value and the VAT amount
description: Learn how to split the realized exchange difference amount into the difference of the invoice net value and the value-added tax (VAT) amount for Poland in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/05/2026
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2020-04-01
---

# Split the realized exchange difference amount into the difference of the invoice net value and the VAT amount

[!include [banner](../../includes/banner.md)]

This article explains how to split the realized exchange difference amount into the difference of the invoice net value and the value-added tax (VAT) amount for Poland in Microsoft Dynamics 365 Finance.

The **Split the AP/AR realized exchange difference amount into the difference of the invoice net value and the VAT amount** feature lets you split the amount of an Accounts payable (AP) and Accounts receivable (AR) foreign currency revaluation into two parts:

- The exchange difference that is related to the net value of the invoice (customer debts and vendor liabilities)
- The exchange difference that is related to the value-added tax (VAT) amount of the invoice

You can also post the exchange differences that are related to the VAT invoice amount to a separate ledger account of realized gains and losses.

This feature is available only in legal entities that have a Polish country/region context.

## Setup

### Activate the feature

In the **Feature management** workspace, turn on the following feature: **(Poland) Split the AP/AR realized exchange difference amount into the difference of the invoice net value and the VAT amount**.

### Set up ledger accounts

To set up a ledger account that you can use to post the exchange difference amount related to the tax amount of the invoice, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** > **Currencies** > **Currency revaluation accounts**. 
1. On **Currency revaluation accounts**, select the currency code. In the **Ledger** field, select the code of the legal entity.

    :::image type="content" source="../media/Currency-revaluation-accounts.png" alt-text="Screenshot of the Currency revaluation accounts page.":::

1. Select a line where the **Posting** field is set to **Realized gain** or **Realized loss**.
1. Set up the main account, and select the ledger account to post the realized exchange difference to.
1. In the **Sales taxes** field, select **Expense** to post part of the realized exchange difference amount that relates to the tax amount of the invoice to a separate expense ledger account. 
1. In the **Tax posting account** field, select the same expense ledger account.

## Post and settle customer and vendor transactions

Post and settle documents in the usual way. The exchange difference transaction that you create during settlement generates a voucher. The exchange difference amount that relates to the tax amount is posted separately to the ledger account that you selected in the **Tax posting account** field on **Currency revaluation accounts**.

## Known limitations

Don't use this feature if you post vendor invoices by using the **Invoice register** and **Invoice approval** journals.

## Examples

The following two examples show the resulting ledger transactions.

### Example 1

Complete the following setup in the **DEMF** legal entity.

1. Change the country/region to **POL**.
1. On the **Ledger** page, verify that the **Accounting currency** field is set to **EUR**.
1. Set up currency exchange rates for the **Default** exchange rate type, as shown in the following table.

    | Date             | US dollars (USD) | Euros (EUR) | Description        |
    |------------------|------------------|-------------|--------------------|
    | January 1, 2020  | 100              | 80          | 100 USD for 80 EUR |
    | January 10, 2020 | 100              | 90          | 100 USD for 90 EUR |

1. Set up ledger accounts for the realized exchange difference in the main account and the tax posting account.

Post the following transactions.

| Document | Date | Amount in USD | Amount in EUR | Voucher | Voucher amount |
|----------|------|---------------|---------------|---------|----------------|
| Customer invoice | January 1, 2020 | 119 USD, which includes a VAT amount of 19 USD | 95.20 EUR, which includes a VAT amount of 15.20 EUR | Debit *AR* | 95.20 |
| | | | | Credit *Expense* | 80.00 |
| | | | | Credit *VAT* | 15.20 |
| Customer payment | January 10, 2020 | 119 USD | 107.10 EUR | Debit *Bank* | 107.10 |
| | | | | Credit *AR* | 107.10 |
| Invoice and payment settlement | January 10, 2020 | 0 USD | 11.90 EUR | Debit *AR* | 11.90 |
| | | | | Credit *Exchange difference – main account* | 10.00 |
| | | | | Credit *Exchange difference – tax posting account* | 1.90 |

In this example:

- 10.00 (= 11.90 × 80.00 ÷ 95.20) is the exchange difference that relates to the net value of the invoice.
- 1.90 (= 11.90 – 10.00) is the exchange difference that relates to the tax amount of the invoice.

### Example 2

Complete the following setup in addition to the setup that you completed for example 1.

1. On the **Ledger** page, in the **Bank exchange rate** field, select **Average**. This rate is used to calculate VAT amounts.
1. Set up the currency exchange rate for the **Average** exchange rate type, as shown in the following table.

    | Date             | USD | EUR | Description         |
    |------------------|-----|-----|---------------------|
    | January 1, 2020  | 100 | 100 | 100 USD for 100 EUR |
    | January 10, 2020 | 100 | 110 | 100 USD for 110 EUR |

Post the following transactions.

| Document | Date | Amount in USD | Amount in EUR | Voucher | Voucher amount |
|----------|------|---------------|---------------|---------|----------------|
| Customer invoice | January 1, 2020 | 119 USD, which includes a VAT amount of 19 USD | 95.20 EUR, which includes a VAT amount of 19.00 EUR | Debit *AR* | 95.20 |
| | | | | Credit *Expense* | 80.00 |
| | | | | Credit *VAT* | 15.20 |
| | | | | Debit *AR tax difference* | 3.80 |
| | | | | Credit *VAT tax difference* | 3.80 |
| Customer payment | January 10, 2020 | 119 USD | 107.10 EUR | Debit *Bank* | 107.10 |
| | | | | Credit *AR* | 107.10 |
| Invoice and payment settlement | January 10, 2020 | 0 USD | 11.90 EUR | Debit *AR* | 11.90 |
| | | | | Credit *Exchange difference – main account* | 10.00 |
| | | | | Credit *Exchange difference – tax posting account* | 1.90 |

In this example:

- 10.00 (= 11.90 × 80.00 ÷ 95.20) is the exchange difference that relates to the net value of the invoice.
- 1.90 (= 11.90 – 10.00) is the exchange difference that relates to the tax amount of the invoice.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
