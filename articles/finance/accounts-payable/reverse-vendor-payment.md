---
# required metadata

title: Reverse a vendor payment
description: This article describes the differences between reversing, deleting, voiding, and rejecting a payment and how to reverse a vendor check. 
author: angelad116
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankChequeTable, LedgerJournalTransBankChequeReversal, LedgerJournalTransVendPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheelo
# ms.tgt_pltfrm: 
ms.assetid: 9f0a1883-cbe0-4cc7-b9f3-dd12fb85ebe8
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Reverse a vendor payment

[!include [banner](../includes/banner.md)]

This article describes the differences between reversing, deleting, voiding, and rejecting a payment. Additionally, it explains the two methods for reversing a vendor check. 

Occasionally, after a vendor payment has been posted, the payment must be reversed. Reversal differs from deleting, voiding, or rejecting a payment. You can delete a payment only if its status is **Created**. This status indicates that the payment has been created but hasn't yet been generated. This limitation always applies, regardless of the method of payment. You can void unposted checks after they have been generated but before they have been posted. If the generated payment is done as an electronic fund transfer (EFT), you can reject the payment before it's posted. To reject a payment, change the **Payment status** value. A payment that has been voided or rejected can be regenerated after the **Payment status** value is changed back to **None**. 

After a payment is posted, reversals are used. Payments that are made electronically can't be reversed after they have been posted. Instead, a new transaction must be created for the amount of the payment to get the liability back on the vendor's account. There are two methods for reversing posted checks. In one method, reversals are posted immediately when you click **Payment reversal** on the **Check** page. In the other method, when you click **Payment reversal** on the **Check** page, the reversal is sent to the check reversal journal in Cash and bank management, where a reviewer can then post or reject the reversal. 

To learn which method your organization uses, view the **Cash and bank management parameters** page. If the **Use review process for payment reversals** option is set to **Yes**, reversals are sent to the check reversal journal for review. The following table describes how the check reversal methods differ.

| If your organization doesn't review check reversals before posting                                                                                                                                  | If your organization reviews check reversals before posting                                                                                                                                                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The check is reversed immediately when you click **OK** on the **Check** page.                                                                                                                      | The check isn't immediately reversed. A check reversal journal is created for review. If the check reversal journal is deleted, the check can be reversed again.                                                                                                                                                                                                                                                                |
| The accounting entries for the original check are reversed.                                                                                                                                         | The ledger account from the original check's accounting entry might not be posted. The financial dimensions from the original check’s journal are used as the default financial dimensions on the check reversal journal. You can change these default values. When the check reversal journal is posted, the main accounts for Accounts payable are entered automatically from the posting profiles, which might have changed. |
| The accounting structures that were used when the original check was posted are used to reverse the check, even if the account structure has been changed. The account combination isn't validated. | If an account structure changed after the original check was posted, a new financial dimension might be required for the reversal of the check. This financial dimension might not be entered automatically from the original payment's journal. The account combination is validated when the check reversal is posted.                                                                                                        |
| Fixed dimensions aren't applied to the reversal, to help guarantee that the same ledger accounts are reversed.                                                                                      | Fixed dimensions are applied to the check reversal journal during posting. The financial dimension value might not exist in the accounting entry for the original check, depending on when the fixed dimension was defined.                                                                                                                                                                                                     |

## Reverse posted checks without reviewing them
If your organization wants to post check reversals immediately when you click **Payment reversal** on the **Checks** page. On the **Cash and bank management parameters** page, set the **Use review process for payment reversals** option to **No**. On the **Checks** page, you can select the check to reverse and select **Payment reversal**. You can then enter the date, and select a reason for the reversal.

## Reverse posted checks after they are reviewed in the check reversal journal
If your organization wants to review check reversals before they are posted, create a check reversal journal for review and on the **Cash and bank management parameters** page, set the **Use review process for payment reversals** option to **Yes**. On the **Checks** page, you can select check to reverse, select **Payment reversal**. You can then enter the date, and select a reason for the reversal. The financial reason must be set up for both Bank and Vendor types. You must also select a journal name to create a journal in the check reversal journal.

### Review a reversal

If you're a user who must review reversals, You can either approve and post the journal, or reject the reversal by deleting the journal. On the **Check reversals journal** page, you can select the reversal journal to review, and then click **Lines**. You can review the reversed check, and then select one of the following approval options:

-   To approve and post the reversal journal, click **Post** or **Post and transfer**.
-   To reject the reversal, delete the reversal check journal.

> [!NOTE]
> If you delete the journal, the reversal is removed from the system, but the original check remains on the **Check** page. The status of the check is no longer **Pending cancellation**.

## Results of posting a reversal
When you post a check reversal, the following events occur:

-   The check status is updated to **Cancellation**.
-   If the **Reconcile** option was selected on the reversal page during the reversal, the check is reconciled (the **Reconciled** option is selected) and doesn't appear on the **Account reconciliation** page.
-   The reversal voucher is posted against the bank account that the check was issued from, to increase the bank account balance.
-   The voucher is posted to General ledger.
-   The modification details are updated in the **History** field group on the **Check** page.

> [!NOTE] 
> When you reverse a check that was issued for an intercompany trade transaction, the offsetting entries come from the accounting setup for intercompany trade, not from the original transaction. If the check that was reversed was issued for a vendor payment, the following events also occur:

-   The original payment from the invoice that the payment was settled against is unapplied (the settlement is reversed).
-   A transaction is posted against the vendor account for the payment reversal, and the reversed payment is settled against the original payment. The **Last settlement voucher** field on the **Vendor transactions** page for the original vendor disbursement is updated to reflect the voucher number of the reversed transaction.

If the check that was reversed was issued for a customer refund, the following events also occur:

-   A transaction is posted against the customer account for the payment reversal, and the settlement between the original payment and the document that the payment was originally settled against is reversed (a negative payment is created).
-   A payment reversal is applied to the original payment. The **Last settlement voucher** field on the **Customer transactions** page for the original customer payment is updated to reflect the voucher number of the reversed transaction.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
