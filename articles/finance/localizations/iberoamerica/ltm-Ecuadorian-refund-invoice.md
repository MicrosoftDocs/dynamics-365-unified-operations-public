---
title: Post Ecuadorian refund invoice transactions
description: Learn how to configure and use refund invoices for Ecuador.
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe

---

# Post Ecuadorian refund invoice transactions

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure and use refund-type invoices for Ecuador. A refund invoice enables an intermediary to purchase goods and services from a vendor on behalf of another party that is referred to as the beneficiary. The beneficiary then reimburses the intermediary for the invoice amount.

## Prerequisites

Before you complete the procedures in this article, the following prerequisites must be met:

- You must configure document class types and document classes that represent the fiscal documents. In this case, the fiscal documents are refund invoices, credit notes, and debit notes.
- An intermediary vendor must be set up.

## Complete the configuration for refund invoices

To complete the configuration for refund invoices, follow these steps.

1. Create document class types and document classes for invoices, credit notes, and debit notes. The new document classes are used exclusively for refund invoices. For each document class, ensure that the **Details Taxpayer** option on the **General** tab is set to **Yes**. This setting enables further configuration on the **Additional data** tab. For example, you can specify the company name, country, or country document type.
1. Create a ledger account to use as a suspense account. Set the main account type to **Profit and loss**.
1. Create a general document class type where both debit and credit options are activated for ledger and vendor journals.
1. Create a general document class that is associated with the previously created document class type that is used exclusively for settlement.

## Run the required transactions

To run a refund invoice in finance and operations apps, three unique transactions are required. The first invoice registers the transaction with the intermediary. The second invoice registers the transaction between the intermediary and the vendor. The third invoice is only for ledger purposes.

> [!NOTE]
> Multiple transactions to the vendor can be refunded simultaneously. However, the total amount of the second group of transactions must equal the amount of the first (intermediary) and last (ledger) transactions.

### Create the first transaction

To create the first transaction, follow these steps.

1. Go to **Account payable** \> **Invoices** \> **Invoice Journal**. All further transactions will be created from this journal.
1. Select **New**, and define the journal name.
1. Go to the lines to set up the transaction. For the first line, define the vendor account with the intermediary vendor. Define the amount, and configure the LATAM fields by using the document class that isn't a **Details Taxpayer** document class.
1. For the second line, use **Ledger**, and select the refund account that you previously created. Add a sales tax group and an item sales tax group as required.
1. Post the transaction.

> [!NOTE]
> Refund type invoices can't be created from purchase orders.

### Create the second transaction 

You must define the same vendor that you used in the first transaction.

To create the second transaction, follow these steps.

1. Complete the LATAM fields by using the **Details Taxpayer** document class that you previously created. In this way, you can complete the fiscal information for the actual vendor of the transaction.
1. Add a debit account of your choice, and configure tax groups and tax codes.
1. Post the transaction.

### Create the third transaction

The third transaction reconciles the accounts that were used in the previous two transactions.

To create the third transaction, follow these steps.

1. The vendor account is credited, and the ledger account is debited with the refund account that was used in the first transaction. Complete the tax groups and codes for the ledger account.
1. Fill in the LATAM fields for the vendor line by using the document class for settlement that you previously created.
1. Post the transaction.

### Initiate vendor transaction settlement

To initiate vendor transaction settlement, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**.
1. Select the vendor account that was used in the transactions. Then, on the vendor header, go to **Transactions**.
1. Settle transactions 1 and 3.

### Set up the transaction relation

To set up the transaction relation, follow these steps.

1. Go to **Account payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**.
1. Search for transaction 1, go to **LATAM option**, select the source document, and then select **New**.
1. Search for the second transaction, and then select **Save**.

## Voucher examples

For these examples, there is a refund operation for $1,000 that has 12% value-added tax (VAT).

| Transaction 1 | Debit | Credit |
| ------------- | ----- | ------ |
| Intermediary | | 1,120 |
| Vat Credit | 120 | |
| Refund Account | 1,000 | |

| Transaction 2 | Debit | Credit |
| ------------- | ----- | ------ |
| Intermediary (details tax payer) | | 1,120 |
| Vat Credit | 120 | |
| Expenses | 1,000 | |

| Transaction 3 | Debit | Credit |
| ------------- | ----- | ------ |
| Intermediary | 1,120 | |
| Vat Credit | | 120 |
| Refund Account | | 1,000 |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
