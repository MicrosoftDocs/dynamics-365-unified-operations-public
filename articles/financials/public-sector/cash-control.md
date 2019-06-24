---
# required metadata

title: Using cash control limits
description: This topic provides information about using cash control to define transaction limits when there is no cash balance or a transaction would drop the cash balance lower than a predefined amount.
author: velofog
manager: AnnBe
ms.date: 06/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-alpavk
ms.search.validFrom: 2019-6-30
ms.dyn365.ops.version: 10.0.3

---

# Using cash control limits

[!include[banner](../includes/banner.md)]

[!include[banner](../includes/preview-banner.md)]


Cash control allows you to define a limit that prevents transactions from posting if no cash balance is available or if the transaction causes the balance to fall below the defined limit. Accounts payable vendor invoices and General ledger advanced ledger entries are validated when they are created, edited, and posted. If the transaction’s posting would cause the related cash account’s balance to be reduced below the limit defined for the account, the user receives an error message and must change the account to continue.

You can also allow specified user groups to override cash control. If a user in a specified user group receives a warning that the cash balance for the account will be reduced below the limit, he or she can choose to continue with posting the transaction. Users might override the cash control limit when the expenditure must be posted in advance of receiving the funds to cover it; or when an approved transfer must happen, but has not been entered or posted yet.

The cash control limit is compared to the cash control balance (cash account balance minus all posted, unpaid Accounts payable invoices). The limit is surpassed when the cash control balance is less than the cash control limit (threshold).

## Set up cash control
Complete the following steps to set up cash control and cash control accounts. 

1. Go to **General leger** > **Ledger setup** > **General ledger parameters**, and in the **Cash control validation** group, select the **Financial diemension set** that will be used to validate the cash control balances.
2. In the **Cash control override** field, select the user group that can override cash control. This allows users that are in this security group to post transactions that exceed the cash control threshold.
3. Next, go to **General ledger** > **Ledger setup** > **Posting setup** > **Cash control**.
4. Select the **Display account names** check box to view the account names for cash and Accounts payable accounts that you enter in the grid area.
5. Enter each cash account. We recommend that you add all valid cash account financial dimension strings. You can then specify which cash accounts are included in the cash control limitation.
6. In the **Cash account** field, enter the cash account financial dimension string. You must enter all of the account numbers.
7. Select the **Participate** check box to indicate that the cash account financial dimension string is subject to cash control. These cash accounts and the corresponding accounts payable accounts are validated against the cash control configuration rules.
8. **Optional**: In the **Accounts payable** account field, enter the accounts payable account financial dimension string used with vendor invoices. You must enter a complete account number.
9. In the **Threshold** field, enter the amount that must remain in the cash account to pass validation. You can enter a negative number if the cash account is allowed to be overdrawn (more transactions paid than are in the account).

## View accounts in cash control
You can review the current balances of the accounts you defined in the **Cash control configuration** page. Go to **General ledger** > **Inquiries** > **Cash control inquiry**.
The inquiry includes the following information:

- Current cash account balance
- Balance of all posted, unpaid accounts payable invoices that are applied to the cash account's corresponding accounts payable account
- Cash control balance, which is the current cash account balance minus all of the posted, unpaid accounts payable invoices and advanced ledger entries
- Cash control threshold so you can compare the cash control balance to see if paying the accounts payable invoices would put the cash account balance below the threshold

## Process transactions with cash control validation
Cash account balances are validated for accounts payable invoices and advanced ledger entries. The line item amount is validated against the cash and accounts payble accounts that the line's financial distributions are associated with.

> [!Note] 
> Budget control is seperate from cash control and can display unrelated errors.

If the cash threshold will be exceeded, you will receive an error message. The error prevents further processing of the invoice unless a cash control override is allowed.

## Vendor invoice workflow

### Workflow is set up for autoposting
When you are using cash control functionality with Accounts payable vendor invoice workflow and workflow is set up for autoposting, at the autoposting step, the system validates whether the submitting user has privileges to override the cash control threshold. 
If the invoice will exceed the cash control threshold and the user has override privileges, the invoice will be automatically posted as part of the workflow process. If the user does not have override privileges, an error message appears in workflow history for the related vendor invoice. For the invoice to be successfully processed through posting, either: 

- A user who has override privileges must resubmit the invoice, or
- The invoice must be changed so that a different cash account is used, or
- The cash control balance must be changed.

### Workflow is not set up for autoposting
When using cash control functionality with Accounts payable vendor invoice workflow and workflow is not set up for autoposting, when the user submits an invoice to workflow and the user has override privileges, the invoice can be submitted to workflow. The cash control vlaidation is performed again when the invoice is posted. This is because cash balances might have changed between the time that the invoice was submitted to workflow and the time of the invoice posting. 

If the threshold will be exceeded and the user does not have privileges to override the cash control limit, an error message appears and the invoice can't be submitted to workflow. For the invoice to be successfully submitted, either a user who has override privileges must resubmit the invoice, the invoice must be changed so that a different cash account is used, or the cash control balance must be changed.
