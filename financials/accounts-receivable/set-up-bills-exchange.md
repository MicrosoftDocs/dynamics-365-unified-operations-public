---
# required metadata

title: Set up bills of exchange
description: This topic describes the steps for setting up bills of exchange.
author: twheeloc
manager: AnnBe
ms.date: 2017-02-08 21 - 05 - 51
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2231
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 269964
ms.assetid: f2077165-da90-4359-ab12-e05717728dc7
ms.search.region: global
# ms.search.industry: 
ms.author: abruer
ms.dyn365.ops.intro: 01-11-2016
ms.dyn365.ops.version: Version 1611

---

# Set up bills of exchange

This topic describes the steps for setting up bills of exchange.

A bill of exchange is a written or electronic order from a customer that specifies that another party, usually a bank, should pay a stated amount to the company. When you use a bill of exchange as payment for a sales order invoice or free text invoice, you credit the customer account. That credit is secured by the bill of exchange until the customer pays the bill of exchange to the bank. Typically, you will settle the invoice with the bill of exchange on the due date. When you receive notification from your bank that the bill of exchange has been honored, you can close the bill of exchange. You can draw a bill of exchange through your bank at either of the following times:

-   On the due date. This approach is known as remit for collection.
-   Before the due date, typically on the discount date that is specified in the terms of payment that are set up for the customer. When you post the transaction, the discount amount is posted to an expense account. The remaining amount is a liability to you until the bank receives payment from the customer. This approach is known as remit for discount.

## Set up posting profiles for bills of exchange
Use the **Customer posting profiles** page to set up posting profiles that you can use with bills of exchange, protest bills of exchange, remittances for collection, and remittances for discount. In the **Summary account** field, select the summary account to post bill of exchange amounts to. This account is debited or credited, depending on the type of bill of exchange transaction:
-   For bills of exchange, this account is debited when a bill of exchange is posted, and it's credited when a remittance for discount or a remittance for collection is posted.
-   For protest bills of exchange, this account is debited when a protest bill of exchange is posted.
-   For remittances for collection, this account is debited when a remittance for collection is posted.
-   For remittances for discount, this account is debited when a remittance for discount is posted.

In the **Settle account** field, select the cash account to post bill of exchange amounts to. This account is debited when a bill of exchange is settled. In the **Sales tax prepayments** field, select the summary account to post sales tax amounts to when bills of exchange are used for prepayments. In the **Liabilities for discount account** field, select the account to post the discount amount for remittances for discount to. This account is credited when a remittance for discount is posted.

## Set up Accounts receivable parameters for bills of exchange
On the **Accounts receivable parameters** page, the default posting profiles for bills of exchange are entered on the **Ledger and sales tax** tab. Number sequences are defined on the **Number sequences** tab.
Set up journal names for bills of exchange
------------------------------------------

On the **Journals names** page, create at least five journal names to use for bills of exchange. Here are the journal types:
-   **Customer draw bill of exchange** – Create a journal name for the Draw bill of exchange journal.
-   **Customer protest bill of exchange** – Create a journal name for the Protest bill of exchange journal.
-   **Customer redraw bill of exchange** – Create a journal name for the Redraw bill of exchange journal.
-   **Customer bank remittance** – Create a journal name for the Remittance journal.
-   **Customer settle bill of exchange** – Create a journal name for the Settle bill of exchange journal.

On the journal voucher page for each bill of exchange journal, enter information about the bill of exchange on the **Bill of exchange** tab. After the bill of exchange journal lines are posted, you can view them on the **Bill of exchange journal inquiry** page and the **Bills of exchange statistics** page.
Set up methods of payment for bills of exchange
-----------------------------------------------

On the **Methods of payment** page, set up at least one method of payment for bills of exchange. If you do business with more than one bank, set up a method of payment that corresponds to the remittance format that each bank requires for bills of exchange.
Set up payment fees for bills of exchange
-----------------------------------------

A payment fee is a charge that is associated with the process of collecting payments from customers. Multiple payment fee setup lines can be associated each payment fee. You can use setup lines to control how default amounts for payment fees are calculated. For example, you can create setup lines for methods of payment, payment specifications, currencies, and time periods. You can also create setup lines for a percentage or amount that is based on day intervals. For example, you can set up an interest percentage that is based on the length of time a payment is overdue. If the bank charges different fees for different remittance types, such as **Collection** or **Discount**, set up a separate payment fee line for each remittance type.
Set up remittance fees for bank remittance files
------------------------------------------------

On the **Bank accounts** page, you can set up remittance fees that a bank charges for each remittance file that is generated. The remittance fees are posted when the remittance has been confirmed and the realized fee amounts are known. Remittance fees differ from payment fees, which are collected from customers and attached to journal lines.
Set up document layouts for bills of exchange
---------------------------------------------

On the **Bank accounts** page, click **Set up**, and specify the document layout that is required for each bank account that you will generate printed bills of exchange documents for.
Set up customers for bills of exchange
--------------------------------------

On the **Customers** page, for each customer who has agreed to pay by using a bill of exchange, you can set up a default method of payment for bills of exchange on the **Payment defaults** tab.



