---
title: Reverse a vendor payment
description: Learn about the differences between reversing, deleting, voiding, and rejecting a payment and how to reverse a vendor check. 
author: mukumarm
ms.author: mukumarm
ms.topic: article
ms.date: 07/13/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: BankChequeTable, LedgerJournalTransBankChequeReversal, LedgerJournalTransVendPaym
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9f0a1883-cbe0-4cc7-b9f3-dd12fb85ebe8
---

# Reverse a vendor payment

[!INCLUDE [banner](../includes/banner.md)]

This article describes the differences between reversing, deleting, voiding, and rejecting a payment. It also explains the two methods for reversing a vendor check.

Occasionally, after you post a vendor payment, you must reverse the payment. Reversal differs from deleting, voiding, or rejecting a payment. You can delete a payment only if its status is **Created**. This status indicates that the payment is created but not yet generated. This limitation always applies, regardless of the method of payment. You can void unposted checks after they're generated but before they're posted. If the generated payment is an electronic fund transfer (EFT), you can reject the payment before it's posted. To reject a payment, change the **Payment status** value. A payment that you void or reject can be regenerated after you change the **Payment status** value back to **None**.

To learn which method your organization uses, view the **Cash and bank management parameters** page. If the **Use review process for payment reversals** option is set to **Yes**, reversals are sent to the check reversal journal for review. The following table describes how the check reversal methods differ.

| If your organization doesn't review check reversals before posting | If your organization reviews check reversals before posting  |
|---------------------------------|-------------------------------------------------------------------------------------|
| The system reverses the check immediately when you select **OK** on the **Check** page.  | The system doesn't immediately reverse the check. A check reversal journal is created for review. If you delete the check reversal journal, you can reverse the check again.        |
| The system reverses the accounting entries for the original check.   | The ledger account from the original check's accounting entry might not be posted. The financial dimensions from the original check’s journal are used as the default financial dimensions on the check reversal journal. You can change these default values. When you post the check reversal journal, the main accounts for Accounts payable are entered automatically from the posting profiles, which might have changed. |
| The system uses the accounting structures that were used when the original check was posted to reverse the check, even if the account structure changed. The account combination isn't validated. | If an account structure changed after the original check was posted, a new financial dimension might be required for the reversal of the check. This financial dimension might not be entered automatically from the original payment's journal. The account combination is validated when the check reversal is posted.     |
| Fixed dimensions aren't applied to the reversal, to help guarantee that the same ledger accounts are reversed.  | Fixed dimensions are applied to the check reversal journal during posting. The financial dimension value might not exist in the accounting entry for the original check, depending on when the fixed dimension was defined.         |

## Reverse posted checks without reviewing them

If your organization wants to post check reversals immediately, follow these steps:

1. On the **Checks** page, select **Payment reversal**.
1. On the **Cash and bank management parameters** page, set the **Use review process for payment reversals** option to **No**.
1. On the **Checks** page, select the check to reverse.
1. Select **Payment reversal**.
1. Enter the date, and select a reason for the reversal.

## Reverse posted checks after they're reviewed in the check reversal journal

If your organization wants to review check reversals before posting, follow these steps: 
1. Create a check reversal journal for review.
2. On the **Cash and bank management parameters** page, set the **Use review process for payment reversals** option to **Yes**.
3. On the **Checks** page, select the check to reverse.
1. Select **Payment reversal**.
1. Enter the date, and select a reason for the reversal. You must set up the financial reason for both Bank and Vendor types. You must also select a journal name to create a journal in the check reversal journal.

### Review a reversal

If you review reversals, you can either approve and post the journal, or reject the reversal by deleting the journal. On the **Check reversals journal** page, select the reversal journal to review, and then select **Lines**. Review the reversed check, and then select one of the following approval options:

- To approve and post the reversal journal, select **Post** or **Post and transfer**.
- To reject the reversal, delete the reversal check journal.

> [!NOTE]
> If you delete the journal, the reversal is removed from the system, but the original check remains on the **Check** page. The status of the check is no longer **Pending cancellation**.

## Results of posting a reversal

When you post a check reversal, the following events occur:

- The check status updates to **Cancellation**.
- If you select the **Reconcile** option on the reversal page during the reversal, the check is reconciled (the **Reconciled** option is selected) and doesn't appear on the **Account reconciliation** page.
- The reversal voucher posts against the bank account that the check was issued from, to increase the bank account balance.
- The voucher posts to General ledger.
- The modification details update in the **History** field group on the **Check** page.

> [!NOTE]
> When you reverse a check that you issued for an intercompany trade transaction, the offsetting entries come from the accounting setup for intercompany trade, not from the original transaction. If the check that you reversed was issued for a vendor payment, the following events also occur:

- The original payment from the invoice that the payment settled against is unapplied (the settlement is reversed).
- A transaction posts against the vendor account for the payment reversal, and the reversed payment settles against the original payment. The **Last settlement voucher** field on the **Vendor transactions** page for the original vendor disbursement updates to reflect the voucher number of the reversed transaction.

If the check that you reversed was issued for a customer refund, the following events also occur:

- A transaction posts against the customer account for the payment reversal, and the settlement between the original payment and the document that the payment originally settled against is reversed (a negative payment is created).
- A payment reversal is applied to the original payment. The **Last settlement voucher** field on the **Customer transactions** page for the original customer payment updates to reflect the voucher number of the reversed transaction.

## Troubleshooting

### Issue: Check reversal journal can't post due to account structure changed

#### Symptom

You can't post a check reversal journal and see the error message: "Ledger account %1 with record ID %2 doesn't match the current account and/or advanced rule structure associated with structure %3. You must update the account to reflect the active structures."

#### Cause

You changed the account structure after creating the reversal journal but before posting the reversal journal. During the check reversal journal posting, the system can't find the account structure, so the posting process fails.

#### Resolution

1. **Delete** the check reversal journal that you can't post.
1. Disable the parameter "**Use review process for payment reversals**" on the **Cash and bank management parameters** form.
1. **Reverse** the check again.

### Issue: "No more checks for account" error when printing checks

#### Symptom

You can't print checks. During check generation, the system displays the following error message: **No more checks for account**.

#### Cause

This problem occurs when you configure the bank account to use the **Fixed** check number method but don't have enough checks with **Created** status available for the bank account.

When the number of available checks is less than the number of checks that you must generate from the payment journal, check generation is blocked.

#### Resolution

To resolve the problem, verify the check number method for the bank account, review the number of available checks, and create more checks if needed.

To verify the check number method for the bank account, follow these steps:

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. Select the relevant bank account.
1. On the **Set up** tab, select **Layout**.
1. On the **Check** FastTab, review the **Check number method** field.
1. Confirm that the value is set to **Fixed**.

To verify the number of available checks, follow these steps:

1. Go to **Cash and bank management** > **Payment reversals** > **Checks**.
1. Filter the records by the relevant bank account.
1. Set the **Status** filter to **Created**.
1. Enable **Include checks without dates**.
1. Compare the number of filtered checks with the number of checks that you're trying to generate from the payment journal.

If the number of checks with **Created** status is less than the number of checks required for the payment journal, the system displays the **No more checks for account** error message and blocks check generation.

To create more checks for the bank account, follow these steps:

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. Select the relevant bank account.
1. On the **Set up** tab, select **Check numbers**.
1. Enter the number of checks to create.
1. Make sure that the quantity is greater than or equal to the number of checks that you must print.
1. Create the checks.
1. Generate the payment checks again.

#### Result

After you create more checks with **Created** status, check generation can continue successfully for the payment journal.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
