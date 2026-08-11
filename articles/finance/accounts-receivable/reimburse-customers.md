---
title: Reimburse customers
description: Learn how to create reimbursement transactions for a group of customers, including a table that describes various prerequisites.  
author: JodiChristiansen
ms.author: jchrist
ms.topic: how-to
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: LedgerJournalTransCustPaym, LedgerJournalTransVendPaym
ms.search.validFrom: 2016-02-28
ms.assetid: 53533ee3-470e-458a-ac8b-3815aa4cb502
---

# Reimburse customers

[!include [banner](../includes/banner.md)]

This article explains how to create reimbursement transactions for a group of customers. If a customer has a credit balance, you can reimburse the customer for the amount of the balance.

> [!NOTE]
> To streamline the process of reimbursement and avoid manual, time-consuming methods, Microsoft introduced a feature that allows for direct refunds to clients from the customer payments journal by using the International Organization for Standardization (ISO) 20022 credit transfer format. This feature generates payment files in the ISO 20022 credit transfer format for customers based on accounts receivable transactions. This functionality is particularly useful if you need to generate Single Euro Payments Area (SEPA) or generic ISO 20022 payments. For more information, see [Refund payment processing in Customer payment journal](refund-customers.md).

The following table shows the prerequisites that must be in place before you start.

| Prerequisite                                                            | Description |
|-------------------------------------------------------------------------|-------------|
|Specify the minimum reimbursement amount for the legal entity.|On the **Accounts receivable parameters** page, in the **General** area, in the **Minimum reimbursement** field, enter the minimum amount that can be reimbursed for customer overpayments.|
| Optional: Add a vendor account to each customer that can be reimbursed. | On the **Customers** page, on the **Miscellaneous details** FastTab, in the **Vendor account** field, select the vendor account for the customer. |

When you create reimbursement transactions, the system creates a vendor invoice for the amount of the credit balance. The reimbursement process removes the credit balance for the customer account and creates a balance due for the vendor account that corresponds to the customer.

1. In Accounts receivable, run the **Reimbursement** process (**Accounts receivable \> Periodic tasks \> Reimbursement**).
1. To group all transactions regardless of ledger dimensions, set the **Summarize customer** option to **Yes**. To group only transactions that have similar ledger dimensions, set the option to **No**.
1. Select **Include customers with outstanding debit transactions** to select customers who have unsettled debit amounts.
1. To reimburse specific customer accounts, on the **Records to include** FastTab, select **Filter**, and then specify the customer accounts in the query.

    The credit amounts are transferred to the vendor accounts of the customers and are processed as ordinary payments. If a customer doesn't have a vendor account, the system automatically creates a one-time vendor account for the customer.

1. To view the reimbursement transactions that were created, use the **Reimbursement** report (**Accounts Receivable \> Inquiries and reports \> Reimbursement report**).
1. In Accounts payable, create a payment for the vendor invoices that the reimbursement process created. For information about how to pay vendors, see [Vendor payment overview](../accounts-payable/Vendor-payments-workspace.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
