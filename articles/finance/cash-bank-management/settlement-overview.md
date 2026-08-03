---
title: Settlement overview
description: Learn about the settlement process, including outliens about transaction types that can be settled and the timing and process for settling them.
author: mukumarm
ms.author: mukumarm
ms.topic: overview
ms.date: 07/20/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: CustOpenTrans, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, VendOpenTrans
ms.dyn365.ops.version: 8.1
ms.assetid: 0968fa71-5984-415b-8689-759a0136d5d1
---

# Settlement overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides general information about the settlement process. It describes which transaction types you can settle, and the timing and process for settling them. It also describes the results of the settlement process.

During settlement, the transactions on one document are applied to the transactions on another document to increase or decrease the balance of each document. For example, you can apply a payment to an invoice. You can settle various types of transactions at different times through different methods. The settlement process can also generate new transactions.

## What transactions can you settle

In Accounts payable and Accounts receivable, you can settle any transaction types that affect the vendor balance or customer balance. These transaction types can include invoices, payments, credit memos, and fees. You can settle any transaction type against any other transaction type. For example, you can settle a payment against an invoice, a credit memo against an invoice, an invoice against another invoice, and a payment against another payment.

You can settle payments against a transaction in the same legal entity or in a different legal entity. In organizations that use a centralized payment model, [centralized payments](set-up-centralized-payments.md) can help streamline the payment process.

## When to settle transactions

You can settle transactions when you enter payments. For example, when you make a payment to a vendor, you typically select which invoices to pay. By selecting invoices, you mark them for settlement against the payment. When Accounts receivable payment clerks record customer payments, they can mark the appropriate invoices for settlement, based on the information that is included with each customer's payment. Use the **Settle transactions** page to mark transactions for settlement. You can open this page from any unposted invoice or payment. When you post the transaction, the settlement is also posted.

You can also settle transactions after posting them. You can enter and post a customer payment without settling it against any invoices. However, you might want to make sure that the payment is settled against the correct invoice before you post the settlement. You can open the **Settle transactions** page from the **All customers** or **All vendors** page, or from the **Transactions** page for any customer or vendor.

You can also reserve posted prepayments for an invoice by marking the payment for settlement against a purchase order or sales order. In this case, the payment still has an open balance, but it can't be settled against another invoice. The payment is automatically settled against the invoice that is created from the purchase order or sales order.

## How to settle transactions

Settle transactions manually, automatically, or by using a combination of the two methods. Choose a settlement method that fits your business processes. On the **Accounts payable parameters** and **Accounts receivable parameters** pages, you can configure the settlement process so that it aligns with those business processes.

You can create vendor payments and customer direct debit payments by using a payment proposal. Use a payment proposal to select invoices to pay. Start the payment proposal manually, and then the system automatically marks the selected invoices for settlement when the payments are created.

If you create payments manually, use the **Settle transactions** page to select invoices for settlement. You can manually select the invoices, or you can use the **Mark by priority** option to have invoices automatically marked for settlement. The **Mark by priority** option is available for Accounts receivable and Accounts payable. Turn on this option on the **Settlement priority** tab of the **Accounts receivable parameters** and **Accounts payable parameters** pages.

If a payment clerk enters a payment but doesn't settle that payment before it's posted, the payment can be automatically settled. Turn on automatic settlement on the **Accounts receivable parameters** and **Accounts payable parameters** pages. Automatic settlement settles transactions only in the same legal entity. It doesn't settle transactions across multiple legal entities.

When you use automatic settlement, you can use the predefined settlement priority, or you can define your own settlement priority on the **Accounts receivable parameters** and **Accounts payable parameters** pages.

## Results of settlement

As you settle transactions, the outstanding balance of each transaction is increased or decreased, as appropriate. Usually, when you settle an invoice and a payment, the status and balance of each transaction update according to the following rules:

- If the payment amount is more than the invoice amount, the invoice balance is reduced to 0.00, and the invoice is closed. The payment remains open, and the balance is the difference between the payment amount and the invoice amount.
- If the payment amount is less than the invoice amount, the payment balance is reduced to 0.00, and the payment is closed. The invoice remains open, and the balance is the difference between the invoice amount and the payment amount.
- If the payment amount equals the invoice amount, both the payment and the invoice are closed, and the balance of both is reduced to 0.00.
- If the balance **summary account** or the **financial dimensions** used for the customer or vendor **invoice** and **payment** transactions differ, the system generates an additional **settlement-type** transaction during **settlement** processing to **offset** the impact of the summary account and financial dimension differences. This process ensures that the customer or vendor balance is correctly cleared and that the summary account and financial dimensions remain balanced.

If the [payment amount is less than the invoice amount](../accounts-payable/vendor-payments-partial-amount.md) because of a cash discount, write-off, or underpayment, the invoice and payment might still be closed, depending on how settlements are configured on the **Accounts payable parameters** and **Accounts receivable parameters** pages.

Settlements can also generate transactions. For example, the settlement of an invoice and a payment might produce a cash discount, realized gain or loss, sales tax adjustments, write-offs, or penny differences.

## Identifying marked transactions during settlement

When you try to settle a transaction, you might notice a symbol that indicates that the transaction is marked in another location. In this case, you can select the transaction on the **Settle transactions** page and then select **Inquiry \> Settlement from the settlement window**. The view for this inquiry shows journals, sales orders, invoices, payment proposals, and customer locations that might be blocking the transaction from settlement. To resolve the issue, you can select the link to go directly from the inquiry to the blocked location. You can then update the document with the adjustments that are required to settle it. You can also use the **Marked** indicator to identify other documents that are included in the same blocking location.

## Large-volume payment settlements

To help prevent performance problems during payment generation, the system displays a warning when the number of open transactions exceeds recommended thresholds. You can review the warning and decide whether to continue processing.

### Payment journal line settlement with more than 2,000 open transactions

When you close the settlement page and the payment journal settles more than 2,000 open transactions, the system displays a warning message:

> The current payment journal line is configured to settle more than 2,000 open transactions. Processing a large number of transactions might affect payment generation performance. Reduce the number of selected transactions before proceeding. Do you want to continue?

You can reduce the number of marked transactions or continue with payment processing.

### Payment proposal processing

When you select **Create payments** on the **Payment proposal** page and the payment proposal contains more than 5,000 open transactions, the system displays a warning: 

> The current payment proposal contains more than 5,000 open transactions. Processing a large number of transactions might affect payment generation performance. Rerun the payment proposal with more restrictive filters or remove open transactions from the current proposal before proceeding. Do you want to continue?

You can rerun the payment proposal with more restrictive filters, remove open transactions from the current proposal, or continue with payment creation.

## Additional resources

- [Settle remainder](settle-remainder.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
