---
# required metadata

title: Settlement overview
description: This article provides general information about the settlement process. It describes which transaction types can be settled, and the timing and process for settling them. It also describes the results of the settlement process.
author: angelad116
ms.date: 07/30/2021
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, VendOpenTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0968fa71-5984-415b-8689-759a0136d5d1
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Settlement overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]


This article provides general information about the settlement process. It describes which transaction types can be settled, and the timing and process for settling them. It also describes the results of the settlement process.

During settlement, the transactions on one document are applied to the transactions on another document to increase or decrease the balance of each document. For example, a payment can be applied to an invoice. Various types of transactions can be settled, at different times, through different methods. The settlement process can also generate new transactions.

## What transactions can be settled

In Accounts payable and Accounts receivable, settlement can occur between any transaction types that affect the vendor balance or customer balance. These transaction types can include invoices, payments, credit memos, and fees. Any transaction type can be settled against any other transaction type. For example, you can settle a payment against an invoice, a credit memo against an invoice, an invoice against another invoice, and a payment against another payment.

You can settle payments against a transaction in the same legal entity or in a different legal entity. In organizations that use a centralized payment model, [centralized payments](set-up-centralized-payments.md) can help streamline the payment process.

## When to settle transactions

Transactions can be settled when payments are entered. For example, when you make a payment to a vendor, you typically select which invoices to pay. By selecting invoices, you mark them for settlement against the payment. When Accounts receivable payment clerks record customer payments, they can mark the appropriate invoices for settlement, based on the information that is included with each customer's payment. You use the **Settle transactions** page to mark transactions for settlement. You can open this page from any unposted invoice or payment. When the transaction is posted, the settlement is also posted. 

Transactions can also be settled after they are posted. You can enter and post a customer payment without settling it against any invoices. However, you might want to make sure that the payment is settled against the correct invoice before you post the settlement. The **Settle transactions** page can be opened from the **All customers** or **All vendors** page, or from the **Transactions** page for any customer or vendor.

You can also reserve posted prepayments for an invoice by marking the payment for settlement against a purchase order or sales order. In this case, the payment will still have an open balance, but it can't be settled against another invoice. The payment will be automatically settled against the invoice that is created from the purchase order or sales order.

## How to settle transactions

Transactions can be settled manually, automatically, or by using a combination of the two methods. The choice of a settlement method depends on your business processes. On the **Accounts payable parameters** and **Accounts receivable parameters** pages, you can configure the settlement process so that it's aligned with those business processes.

You can create vendor payments and customer direct debit payments by using a payment proposal. A payment proposal is used to select invoices to pay. The payment proposal is started manually, and then the system automatically marks the selected invoices for settlement when the payments are created.

If payments are created manually, you can use the **Settle transactions** page to select invoices for settlement. You can manually select the invoices, or you can use the **Mark by priority** option to have invoices automatically marked for settlement. The **Mark by priority** option is available only for Accounts receivable. You can turn on this option on the **Settlement priority** tab of the **Accounts receivable parameters** page.

If a payment clerk enters a payment but doesn't settle that payment before it's posted, the payment can be automatically settled. You can turn on automatic settlement on the **Accounts receivable parameters** and **Accounts payable parameters** pages. Automatic settlement settles transactions only in the same legal entity. It doesn't settle transactions across multiple legal entities.

When you use automatic settlement, you can use the predefined settlement priority, or you can define your own settlement priority on the **Accounts receivable parameters** page. This functionality is available only for Accounts receivable.

## Results of settlement

As transactions are settled, the outstanding balance of each transaction is increased or decreased, as appropriate. Usually, when an invoice and a payment are settled, the status and balance of each transaction is updated according to the following rules:

- If the payment amount is more than the invoice amount, the invoice balance is reduced to 0.00, and the invoice is closed. The payment remains open, and the balance is the difference between the payment amount and the invoice amount.
- If the payment amount is less than the invoice amount, the payment balance is reduced to 0.00, and the payment is closed. The invoice remains open, and the balance is the difference between the invoice amount and the payment amount.
- If the payment amount equals the invoice amount, both the payment and the invoice are closed, and the balance of both is reduced to 0.00.

If the [payment amount is less than the invoice amount](../accounts-payable/vendor-payments-partial-amount.md) because of a cash discount, write-off, or underpayment, the invoice and payment might still be closed, depending on how settlements are configured on the **Accounts payable parameters** and **Accounts receivable parameters** pages.

Settlements can also generate transactions. For example, the settlement of an invoice and a payment might produce a cash discount, realized gain or loss, sales tax adjustments, write-offs, or penny differences.

## Identifying marked transactions during settlement

When you try to settle a transaction, you might notice a symbol that indicates that the transaction is marked in another location. In this case, you can select the transaction on the **Settle transactions** page and then select **Inquiry \> Settlement from the settlement window**. The view for this inquiry shows journals, sales orders, invoices, payment proposals, and customer locations that might be blocking the transaction from settlement. To resolve the issue, you can select the link to go directly from the inquiry to the blocked location. You can then update the document with the adjustments that are required to settle it. You can also use the **Marked** indicator to identify other documents that are included in the same blocking location.

## Resolve issues with transactions that can't be settled

Sometimes, you can't settle transactions because another activity is currently processing the document. If you try to settle the transactions, an error occurs, because those transactions are being used. To fix this issue, you can use the **Marked transaction details** page to find transactions that are marked for settlement and identify any other processes that are accessing them.

Transactions are marked for settlement either when vendor invoices are being paid or when customers pay their open invoices. Occasionally, these invoices might already be marked for settlement. Therefore, users can't select them for payment. The invoices might be marked by another customer payment journal, sales order, vendor payment journal, or purchase order in the current legal entity or another legal entity.

If a transaction is blocked for settlement when you're entering a customer payment, open the **Customer marked transaction details** page (**Accounts receivable \> Periodic tasks \> Customer marked transaction details**). To quickly identify where a transaction is blocked, you can set any of the following selection parameters: **Customer account**, **Voucher**, **Date**, or **Invoice**. If you don't set any selection parameters, the system shows all blocked documents from the current company or another company that you select. After the transaction that has been blocked for settlement is identified, you can select it and then select **Unmark selected transactions**. The selected transaction is then removed from any journal that includes it. However, the document isn't removed from the other location. Only the marking information is removed from that journal.

If a transaction is blocked for settlement when you're entering a vendor payment, open the **Vendor marked transaction details** page (**Accounts payable \> Periodic tasks \> Vendor marked transaction details**). To quickly identify where a transaction is blocked, you can set any of the following selection parameters: **Vendor account**, **Voucher**, **Date**, or **Invoice**. If you don't set any selection parameters, the system shows all blocked documents from the current company or another company that you select. After the transaction is identified, you can select it and then select **Unmark selected transactions** to fix the blocking issue. The selected transaction is then removed from any other journal where it's selected. However, the document isn't removed from the other location. Only the marking information is removed from that journal.

To identify all blocked documents, open the **All marked transaction details** page (**Accounts receivable \> Periodic tasks \> All marked transaction details** or **Accounts payable \> Periodic tasks \> All marked transaction details**). To quickly identify where a transaction is blocked, you can set any of the following selection parameters: **Customer account**, **Vendor account**, **Voucher**, **Date**, or **Invoice**. If you don't set any selection parameters, the system shows all blocked documents from the current company or another company that you select. After the transaction is identified, you can select it and then select **Unmark selected transactions** to fix the blocking issue. The selected transaction is then removed from any other journal where it's selected. However, the document isn't removed from the other location. Only the marking information is removed from that journal.

Before you can use this feature, it must be turned on in your system. Admins can use the **Feature management** workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

- **Module:** Cash and bank management
- **Feature name:** Marked transaction detail form

## Additional resources

- [Settle remainder](settle-remainder.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
