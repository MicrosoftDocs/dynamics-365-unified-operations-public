---
title: Ecuadorian refund invoice transactions posting
description: The article describes how to configure and use refund invoices for Ecuador. 
author: Fhernandez0088
ms.date: 12/30/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe

---

# Ecuadorian refund invoice transactions posting

[!INCLUDE[banner](../../includes/banner.md)]

This article provides a guide on configuring and utilizing refund-type invoices for Ecuador. A Refund invoice enables an intermediary to purchase goods and services from a vendor on our behalf. Subsequently, we reimburse the intermediary for the invoice amount.

## Prerequisites
Before you complete the procedure in this article, the following prerequisites must be met:
* Configure document class types and document classes that represent the fiscal documents. In this case, refund invoice, credit and debit note.
* Intermediary vendor must be set up.


## Configuration for refund invoice

To configuration for refund invoice, follow these steps.

1. Create new document class types and document classes for invoices, credit notes, and debit notes. These document classes are exclusively used for refund invoices. For these document classes, ensure the **Details Taxpayer** option in the **General** tab is set to **Yes**. This setting enables further configurations in the **Additional data** tab. For example, **company name**, **country** or **country document type**.
1. Create a new ledger account to be used as a suspense account. Set the main account type to **Profit and loss**.
1. Create a general document class type with both debit and credit options activated for ledger and vendor journals.
1. Create a general document class associated with the previously created document class type that is used exclusively for settlement.

## Execute the required transactions

To execute a refund invoice in finance and operations apps, three unique transactions are required. The first invoice registers the transaction with our intermediary. The second one registers the transaction between the intermediary and the vendor. The third is solely for ledger purposes.

> [!NOTE]
> Multiple transactions to the vendor can be refunded simultaneously. However, the total amount of the second group of transactions must be equal to the first (intermediary) and last (ledger) transactions.

### Create the first transaction 

To create the first transaction, follow these steps.

1. Go to **Account payable** \> **Invoices** \> **Invoice Journal**. All further transactions will be created from this journal.
1. Select **New**, define the journal name. Go to the lines to set up the transaction.
1. For the first line, define the vendor account with the intermediary vendor. Define the amount and configure the LATAM fields using the non-details taxpayer document class.
1. For the second line, use Ledger and select the refund account previously created. Add a **Sales a tax group** and **Item sales tax group** if needed.
1. Post the transaction.

> [!NOTE]
> Refund type invoices cannot be created from purchase order.

### Create the second transaction 

You must define the same vendor used in transaction number one. 

To create the second transaction, follow these steps.

1. Complete the LATAM fields with the **Details taxpayer-type** document class created in this article. This allows you to complete the fiscal information for the actual vendor of the transaction.
1. Add a debit account of your choice, configure tax group and tax codes.
1. Post the transaction.

### Create the third transaction 

The third transaction reconciles the accounts used in the previous two transactions. 

To create the thrid transaction, follow these steps.

1. The vendor account is credited, and the ledger account will be debited with the refund account used in transaction one.
1. Complete the tax groups and codes for the ledger account and fill in the LATAM fields for the vendor line using the document class for settlement previously created. Post the transaction.
 
### Initiate Vendor transactions settlement

To initiate Vendor transactions settlement, follow these steps.

1. Go to **Accounts payable > Vendors > All vendors** select the vendor account used in the transactions. In the vendor header, go to **Transactions**.
1. Settle Transaction one and three.

### Set up the transaction relation

To set up the transaction relation, follow these steps.

1. Go to **Account payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**.
1. Search for transaction number one, go to LATAM option > source document, select **New**.
1. Search for the second transaction and select **Save**.

## Vouchers examples

Assume a refund operation of $1,000 with a 12% VAT.


| Transaction 1  | Debit |Credit|
| ------------- |:-------------:|:-------------:|
| Intermediary      |      | 1120 |
| Vat Credit      | 120     |
| Refund Account      | 1000     |

| Transaction 2  | Debit |Credit|
| ------------- |:-------------:|:-------------:|
| Intermediary (details tax payer)      |      | 1120 |
| Vat Credit      | 120     |
| Expenses      | 1000     |

| Transaction 3  | Debit |Credit|
| ------------- |:-------------:|:-------------:|
| Intermediary      | 1120     |  |
| Vat Credit      |      |120
| Refund Account      |      |1000

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
