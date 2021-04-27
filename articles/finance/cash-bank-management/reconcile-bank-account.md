---
# required metadata

title: Reconcile a bank account
description: This topic describes how to reconcile a bank account.
author: panolte
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: panolte
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: 10.0.5
---

# Reconcile a bank account

[!include[banner](../includes/banner.md)]

When you receive a bank statement, you should periodically reconcile legal entity bank transactions with the transactions on the bank statement.

You cannot reconcile a bank statement with a bank account if any of the checks or deposit slip payments that are listed on the statement currently have a status of **Pending cancellation**. After a reviewer posts or rejects a check reversal or deposit slip payment cancellation, the status is no longer **Pending cancellation**, and you can reconcile the bank account.

1.  Go to **Cash and bank management** \> **Bank Accounts** \> **Bank accounts**. Select the bank account to reconcile with the bank statement and select **Reconcile** > **Account reconciliation**.

2.  Enter information in the **Bank statement date** and **Bank statement** fields. In the **Ending balance** field, you can enter the balance of the bank account as it appears on the bank statement.

3.  Select **Transactions** to open the **Account reconciliation** page.

4.  For each transaction that is included on the bank statement, select the **Cleared** check box if the amount in Dynamics 365 Finance corresponds to the amount on the bank statement. You can also enter or modify the value in the **Bank transaction type** field. This field value is important for bank transaction statistics and for some reports.
    

    > [!NOTE]
    > <P>Do not select the <STRONG>Cleared</STRONG> check box for transactions that are not on the bank statement. These transactions will continue to be displayed in on this page until they are reconciled with a future bank statement.</P>
    > <P>The <STRONG>Cleared</STRONG> check box is not available if the transaction has a status of <STRONG>Pending cancellation</STRONG>. Transactions might have this status if Finance is set up to require that reversals or cancellations be sent to review before they are posted. After a reviewer posts or rejects the reversal or cancellation, the status is no longer <STRONG>Pending cancellation</STRONG>, and you can reconcile the bank account with the bank statement.</P>

    
    To select the **Cleared** check box for an interval of checks that all are displayed on the bank statement, select **Mark check interval**, and then indicate the interval.

5.  If the amount for a bank account transaction does not correspond to the amount for the transaction on the bank statement, enter the amount of the correction in the **Correction amount** field.
    

    > [!NOTE]
    > <P>If the fiscal period of the transaction to be corrected is closed, the <STRONG>Correction amount</STRONG> field cannot be used. Instead, create a line that has a transaction date that is in an open fiscal period for the correction. In this case, you must add the financial dimensions that were used on the original transaction, and also the offset main account.</P>



6.  Create transactions for entries, such as fees and interest, that are on the bank statement but that are not recorded in Finance. Enter the **Bank transaction type** and appropriate financial dimensions.

7.  As the transactions on the bank statement are marked as **Cleared**, the amount in the **Unreconciled** field, which is recalculated continuously as you make changes, approaches zero. When it reaches zero, select **Reconcile account** to post the reconciliation, and the transactions and corrections that you have created.
    
    After the reconciliation is posted, the transactions that have been included cannot be modified or corrected, and they are not displayed for future account reconciliation.

8.  To view bank transactions that have not yet been reconciled, use the **Unreconciled bank transactions** report. To view the bank statement for a bank account, use the **Bank statement** report.

## Cancel bank statement reconciliation 

The Cancel bank statement reconciliation functionality enables you to cancel bank statement reconciliation. To use this feature, enable the **Cancel bank statement reconciliation** feature in the **Feature management** workspace. You also need to enable the **Allow bank statement edit** parameter. To do this, go to **Cash and bank management > Setup > Cash and bank management parameters > Bank reconciliation**.
 
Bank statement reconciliations can only be canceled in the chronological order in which they were entered. When a bank statement reconciliation is canceled, new transactions and corrections will be reversed and all other transactions will be marked as un-reconciled.
 
To cancel bank statement reconciliation, select the bank statement and select **Bank statement > Cancel bank reconciliation**. On the **Cancel bank reconciliation** page, provide the **Reason code**, **Reason comment**, and **Cancellation date**. Select **OK** to begin cancellation. Note, the bank statement cancellation date must be on or after the bank statement date. After the bank statement reconciliation has canceled, the **Cancellation date** field for the bank statement will be updated with the **Cancellation date** provided. Select the **Transactions** button to view the transactions for which the reconciliation was canceled.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]