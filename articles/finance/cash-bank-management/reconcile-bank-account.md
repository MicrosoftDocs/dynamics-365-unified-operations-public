---
title: Reconcile a bank account
description: Learn about how to reconcile a bank account, including a step-by-step process and an outline on canceling bank statement reconciliation.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 10/10/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 
ms.search.form:
ms.dyn365.ops.version: 10.0.5
---

# Reconcile a bank account

[!include[banner](../includes/banner.md)]

When you receive a bank statement, you should periodically reconcile legal entity bank transactions with the transactions on the bank statement.

You can't reconcile a bank statement with a bank account if any of the checks or deposit slip payments that are listed on the statement currently have a status of **Pending cancellation**. After a reviewer posts or rejects a check reversal or deposit slip payment cancellation, the status isn't **Pending cancellation**, and you can reconcile the bank account.

1. Go to **Cash and bank management** \> **Bank Accounts** \> **Bank accounts**. Select the bank account to reconcile with the bank statement and select **Reconcile** > **Account reconciliation**.

2. Enter information in the **Bank statement date** and **Bank statement** fields. In the **Ending balance** field, enter the bank account balance as it appears on the bank statement.

3. Select **Transactions** to open the **Account reconciliation** page.

4. For each transaction that is included on the bank statement, select the **Cleared** checkbox if the amount in Dynamics 365 Finance corresponds to the amount on the bank statement. You can also enter or modify the value in the **Bank transaction type** field. This field value is important for bank transaction statistics and for some reports. 
    

>[!NOTE]
>Don't select the **Cleared** checkbox for transactions that are not on the bank statement. These transactions will continue to be displayed in on this page until they are reconciled with a future bank statement.
>The **Cleared** checkbox isn't available if the transaction has a status of **Pending cancellation**. Transactions have this status if Finance requires that reversals or cancellations are reviewed before they are posted. After a reviewer posts or rejects the reversal or cancellation, the status is no longer **Pending cancellation**, and you can reconcile the bank account with the bank statement.


To select the **Cleared** checkbox for an interval of checks that all are displayed on the bank statement, select **Mark check interval**, and then indicate the interval.
If all transactions in the list can be cleared, select **Mark all as cleared**.

5.  If the amount for a bank account transaction doesn't correspond to the amount for the transaction on the bank statement, enter the amount of the correction in the **Correction amount** field.
    

> [!NOTE]
> If the fiscal period of the transaction to be corrected is closed, the **Correction amount** field can't be used. Instead, create a line that has a transaction date that is in an open fiscal period for the correction. In this case, you must add the financial dimensions that were used on the original transaction, and also the offset main account.



6.  Create transactions for entries, such as fees and interest, that are on the bank statement but that aren't in Finance. Enter the **Bank transaction type** and appropriate financial dimensions.

7.  As the transactions on the bank statement are marked as **Cleared**, the amount in the **Unreconciled** field, which is recalculated continuously as you make changes, approaches zero. When it reaches zero, select **Reconcile account** to post the reconciliation, and the transactions and corrections.
    
    After the reconciliation is posted, the transactions that have been included can't be modified or corrected, and they're not displayed for future account reconciliation.

8.  To view bank transactions that haven't been reconciled, use the **Unreconciled bank transactions** report. To view the bank statement for a bank account, use the **Bank statement** report.

## Cancel bank statement reconciliation 

The **Cancel bank statement reconciliation** functionality enables you to cancel bank statement reconciliation. You need to enable the **Allow bank statement edit** parameter. To do this, go to **Cash and bank management > Setup > Cash and bank management parameters > Bank reconciliation**.
 
Bank statement reconciliations can only be canceled in the chronological order in which they were entered. When a bank statement reconciliation is canceled, new transactions and corrections are reversed and all other transactions are marked as unreconciled.
 
To cancel bank statement reconciliation, follow these steps:
1. Select the bank statement and select **Bank statement > Cancel bank reconciliation**.
2. On the **Cancel bank reconciliation** page, provide the **Reason code**, **Reason comment**, and **Cancellation date**.
3. Select **OK**.

>[!Note]
> The bank statement cancellation date must be on or after the bank statement date. After the bank statement reconciliation has been canceled, the **Cancellation date** field for the bank statement is updated with the **Cancellation date** provided. Select the **Transactions** button to view the transactions for which the reconciliation was canceled.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
