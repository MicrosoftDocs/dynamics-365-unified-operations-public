---
title: Use cash control limits
description: Learn how to use cash control to define transaction limits when a transaction causes the cash balance to fall below a predefined amount.
author: mukumarm
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/10/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-8-04
ms.search.form:
ms.dyn365.ops.version: 10.0.5
---

# Use cash control limits

[!include [banner](../includes/banner.md)]

This article explains how to use cash control to define transaction limits when there's no cash balance or a transaction causes the cash balance to fall below a predefined amount.

Cash control allows you to define a limit (threshold) to prevent transactions from being posted if no cash balance is available, or if the transaction will cause the balance to fall below the defined limit. The system evaluates the account defined on the consumed posting definition when you create, edit, and post transactions. If there's no generated entry, the system uses the matching account. If posting the transaction causes the related cash account's balance to fall below the limit that you set for the account, the system displays an error message and you must change the account to continue.


The cash control limit is compared to the cash control balance (cash account balance minus all posted, unpaid Accounts payable invoices). When the cash control balance is less than the cash control limit, the limit is exceeded.

## Set up cash control

Follow these steps to set up cash control and cash control accounts.

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. In the **Cash control validation** group, in the **Financial dimension set** field, select the financial dimension set to use to validate cash control balances.
3. In the **Cash control override** field, select the user group that can override cash control. Users in this security group will then be able to post transactions that exceed the cash control limit.
1. In the **Cash control override** field, select the user group that can override cash control. Users in this security group can post transactions that exceed the cash control limit.
5. Set the **Display account names** option to **Yes** to show the account names for cash accounts and Accounts payable accounts that you enter in the grid.
6. Enter each cash account.

We recommend that you add all financial dimension strings for all valid cash accounts. You can then specify which cash accounts are subject to the cash control limit.

1. In the **Cash account** field, enter the cash account financial dimension string. You must enter complete account numbers.
Add all financial dimension strings for all valid cash accounts. You can then specify which cash accounts are subject to the cash control limit.
4. In the **Threshold** field, enter the amount that must remain in the cash account to pass validation. You can enter a negative number if the cash account can be overdrawn (that is, the transaction amounts can exceed the account balance).

## View accounts in cash control

You can review the current balance of the accounts that you defined on the **Cash control configuration** page. Go to **General ledger** > **Inquiries and reports** > **Cash control inquiry**.

The inquiry includes the following information:

- The current cash account balance
- The balance of all posted, unpaid Accounts payable invoices that are applied to the cash account's corresponding Accounts payable account
- The cash control balance, or the current cash account balance minus all posted, unpaid Accounts payable invoices
- The cash control limit, so that you can compare it to the cash control balance and determine whether payment of the Accounts payable invoices causes the cash account balance to fall below the cash control limit

## Process transactions by using cash control validation

The system validates cash account balances for Accounts payable invoices and advanced ledger entries. It validates the line item amount against the cash accounts and Accounts payable accounts that the line's financial distributions are associated with.

[!NOTE] Budget control is separate from cash control and can show unrelated errors.

If the cash control limit is exceeded, the system displays an error message. The error prevents further processing of the invoice unless a cash control override is allowed.

## Vendor invoice workflow

### The workflow is set up for autoposting

When you use the cash control functionality with the Accounts payable vendor invoice workflow, and the workflow is set up for autoposting, the system validates that the user who is submitting the vendor invoice has privileges to override the cash control limit at the autoposting step.

If the invoice exceeds the cash control limit, and the user has override privileges, the invoice is automatically posted as part of the workflow process. If the user doesn't have override privileges, an error message is displayed in the workflow history for the related vendor invoice. In this case, the invoice can be successfully processed through posting only if one of the following conditions is met:

- A user with override privileges resubmits the invoice
- The invoice is changed so that a different cash account is used
- The cash control balance is changed

### The workflow isn't set up for autoposting

When you use the cash control functionality with the Accounts payable vendor invoice workflow, and the workflow isn't set up for autoposting, a user with override privileges can submit an invoice to the workflow. The system performs cash control validation again when the invoice is posted. This second validation is done because cash balances can change between the time when the invoice is submitted to the workflow and the time when the invoice is posted.

If the invoice exceeds the cash control limit and the user doesn't have override privileges, an error message is displayed, and the invoice can't be submitted to the workflow. In this case, the invoice can be successfully submitted only if one of the following conditions is met:

- A user with override privileges resubmits the invoice
- The invoice is changed so that a different cash account is used
- The cash control balance is changed

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
