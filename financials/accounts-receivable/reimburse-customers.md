---
# required metadata

title: Reimburse customers
description: This article explains how to create reimbursement transactions for a group of customers. If a customer has a credit balance, you can reimburse the customer for the amount of the balance. 
author: twheeloc
manager: AnnBe
ms.date: 2015-12-02 23 - 14 - 54
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransCustPaym, LedgerJournalTransVendPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 14191
ms.assetid: af26666f-23af-48aa-a1c4-7d72f7713d7b
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Reimburse customers

This article explains how to create reimbursement transactions for a group of customers. If a customer has a credit balance, you can reimburse the customer for the amount of the balance. 

The following table shows the prerequisites that must be in place before you start.

| Prerequisite                                                            | Description                                                                                                                                                                                 |
|-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Specify the minimum reimbursement amount for the legal entity.          | On the **Accounts receivable parameters** page, in the **General** area, in the **Minimum reimbursement** field, enter the minimum amount that can be reimbursed for customer overpayments. |
| Optional: Add a vendor account to each customer that can be reimbursed. | On the **Customers** page, on the **Miscellaneous details** FastTab, in the **Vendor account** field, select the vendor account for the customer.                                           |

When you create reimbursement transactions, a vendor invoice is created for the amount of the credit balance. The reimbursement process removes the credit balance for the customer account and creates a balance due for the vendor account that corresponds to the customer.

1.  In Accounts receivable, run the **Reimbursement** process.
2.  Follow one of these steps:
    -   To reimburse specific customer accounts, click **Select**, and specify the customer accounts in the query.
    -   To reimburse all customer accounts, click **OK**.

    The credit amounts are transferred to the vendor accounts of the customers and are processed as ordinary payments. If a customer doesn't have a vendor account, a one-time vendor account is automatically created for the customer.
3.  To view the reimbursement transactions that were created, use the **Reimbursement** page.
4.  In Accounts payable, create a payment for the vendor invoices that were created by the reimbursement process.


