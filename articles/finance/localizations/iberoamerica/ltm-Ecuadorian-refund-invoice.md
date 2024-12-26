---
title: Ecuadorian refund invoice transactions posting
description: The article describes how to configure and use refund invoices for Ecuador. 
author: Fhernandez0088
ms.date: 26/12/2024
ms.topic: Article
ms.reviewer: johnmichalak
ms.author: v-federicohe
ms.custom: bap-template
---

# Ecuadorian refund invoice transactions posting
This article provides a guide on configuring and utilizing refund-type invoices for Ecuador. A Refund invoice enables an intermediary to purchase goods and services from a vendor on our behalf. Subsequently, we reimburse the intermediary for the invoice amount.

## Prerequisites
Before you complete the procedure in this article, the following prerequisites must be met:
* Configure document class types and document classes that represent the fiscal documents. In this case refund invoice, credit and debit note.
* Intermediary vendor must be set up.


## Configuration for refund invoice
*	Create new document class types and document classes for invoices, credit notes, and debit notes. These document classes will be exclusively used for refund invoices. For these document classes, ensure the “Details Taxpayer” option in the General tab is set to “Yes.” This setting will enable further configurations in the Additional Data tab such as **company name**, **country** or **country document type**
*	Create a new ledger account to be used as a suspense account. Set the main account type to “Profit and Loss.”
*	Create a general document class type with both debit and credit options activated for ledger and vendor journals.
*	Create a general document class associated with the previously created document class type, which will be used exclusively for settlement.

## Execute the required transactions
To execute a refund invoice in Finance and Operations 365, three unique transactions are required. The first invoice registers the transaction with our intermediary. The second one registers the transaction between the intermediary and the vendor. The third is solely for ledger purposes.

> Note: Multiple transactions to the vendor can be refunded simultaneously. However, the total amount of the second group of transactions must be equal to the first (intermediary) and last (ledger) transactions.

### Transaction 1
1. Go to **Account payable > Invoices > Invoice Journal**. All further transactions will be created from this journal.
2. Click in **New**, define the journal name. Go to lines to set up the transaction
3. For the first line, define the vendor account with the intermediary vendor. Define the amount and configure the LATAM fields using the non-details taxpayer document class.
4. For the second line, use Ledger and select the refund account previously created. Add Sales a tax group and item sales tax group if neccesary. Post the transaction

> Note: Refund type invoices cannot be created from purchase order.

### Transaction 2
You must define the same vendor used in transaction number 1.
1. Complete the LATAM fields with the “details taxpayer-type” document class created in this article. This will allow you to complete the fiscal information for the actual vendor of the transaction.
2. Add a debit account of your choice, configure tax group and tax codes. Post the transaction.

### Transaction 3
The third transaction reconciles the accounts used in the previous two transactions.
1. The vendor account will be credited, and the ledger account will be debited with the refund account used in transaction 1.
2. Complete the tax groups and codes for the ledger account and fill in the LATAM fields for the vendor line using the document class for settlement previously created. Post the transaction.
 
### Vendor transactions settlement:
1.	Go to **Accounts payable > Vendors > All vendors** secelt the vendor account used in the transactions. In the vendor header, go to **Transactions**.
2.	Settle Transaction 1 and 3.

### Transaction relation:
1.	Go to **Account payable > inquiries and reports > invoice > invoice journal**.
2.	Search for transaction number 1, go to LATAM option > source document, click New
3.	Search for the 2nd transaction and click save

## Vouchers examples

Let’s assume a refund operation of $1,000 with a 12% VAT


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
