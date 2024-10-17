---
# required metadata

title: Partial ledger settlements
description: This topic explains how partial ledger settlements can be setup and processed in General ledger. 
author: JodiChristiansen
ms.date: 10/17/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2024-10-17
ms.dyn365.ops.version: 10.0.42

---

# Partial ledger settlements
The Ledger settlement process allows an organization to ‘reconcile’ clearing accounts, to ensure that the amount that is posted into a main account is fully cleared out of that account.  For example, an organization pays an insurance company 12,000 USD in October for a yearly policy.  The 12,000 USD cannot be fully expensed yet because the insurance company hasn’t fulfilled their contractual obligations.  As each month passes, 1,000 USD is recognized as an expense, so 1,000 USD is cleared from the accrued expense account as a credit amount.  That means that the accrued expense account will start with a balance of 12,000 USD debit and each month a 1,000 USD credit will be posted to reduce the balance in the account. After 12 months, the 12,000 USD is cleared and ledger settlement can be completed by marking the 13 transactions, which net to zero. You cannot settle the 12,000 USD debit until all the credits have been posted. When expenses like this cross fiscal years it can be difficult to use ledger settlements and the Advanced awareness option because settlements cannot cross fiscal years. 

In Microsoft Dynamics 365 Finance version 10.0.42, the **Partial ledger settlements** feature is available and resolves the above issue because at the end of the year (or each month/fiscal period), a partial ledger settlement can be done. Using the example above with the insurance policy, at the end of December 3,000 USD has been cleared from the accrued expense account. In the Ledger settlement page, the original 12,000 USD debit and three 1,000 USD credit transactions can be selected and ledger settled. The remaining 9,000 USD will carry forward to the next year to be ledger settled. 

Another benefit of using Partial ledger settlements is **Subledger to ledger auto settlement**. With this option set to **Yes**, any settlements that originate in accounts payable or accounts receivable will automatically be settled in the General ledger. This is explained in detail at the bottom of this page. 

## Partial ledger settlements prerequisites

To use partial ledger settlements the following features must be set to Yes in General ledger parameters:
 - Enable advanced awareness options
 - Enable post currency realized gains/losses for ledger settlements

> [!NOTE]
> In version 10.0.40 the Enable advanced awareness options, Enable post currency realized gains and losses for ledger settlements and the Enable process automation for ledger settlements was moved from Feature management to **General ledger parameters** found under **General ledger > Ledger setup**. 

> [!Important]
> Once the partial ledger settlement feature is enabled (set to **Yes**) it cannot be disabled or turned off because data is migrated to new tables. All prior ledger settlement features that are required cannot be disabled or turned off either. This includes the **Enable advanced awareness options** and **Enable post currency realized gains/losses for ledger settlements**.

The **Enable process automation for ledger settlement** and the **Subledger to ledger auto settlement** can be set to **Yes** or **No** at any time. 

As with the existing Ledger settlements, the main account needs to be added to the list of accounts for partial ledger settlements. The exception to this rule is any account that is settled in the subledger (accounts payable or accounts receivable) does not need to be listed here. If **Subledger to ledger auto settlement** is set to **Yes**, those accounts will be automatically settled and do not need to be listed. If they are added to the list of accounts, you will be able to see those accounts in the Ledger settlements page. 

## Partially settle transactions

With the **Awareness between ledger settlement and year-end close** and the **Partial ledger settlements** features set to **Yes**, the Ledger settlements page changes in the following ways: 
 - The Main account is required as all ledger settlements must be done for transactions in a single main account
 - All ledger settlements must be completed within a fiscal year
 - Change the posting layer as required but you can't settle transactions that are in different posting layers.
 - To show the main account and dimensions separately, select a financial dimension set.
 - The Status filter now has a Partially settled status and you can select more than one status at a time. The status options are All, Not settled, Settled and Partially settled with Not settled being the default.
 - The Accounting currency and Reporting currency totals display at the bottom of the page.
 - The Reverse button has moved to the Ledger settlements history page
 - With partial ledger settlements debits do not need to equal credits to ledger settle so some transactions will have a remaining balance if they are partially settled. Settlement history is now tracked for all transactions, so the following columns have been added to the grid to track this information.
 - History, Amount in reporting currency, Remaining amount in transaction currency, Remaining amount in accounting currency, Remaining amount in reporting currency
 - When a debit transaction is partially settled with a credit transaction, or vice versa, the status of the fully settled transaction will be Settled. If partially settled, the status is Partially settled and the remaining amount columns will display the amount left to settle. One debit transaction can be settled with multiple credit transactions, or vice versa. For example, Voucher GJ00105 is a debit for 1000 USD. Voucher GJ00210 for 700 USD and GJ00236 for 300 USD are marked for settlement with the debit.
 
 table 1

 Once settled, the Settle Id column displays Multiple for the debit transaction because more than one credit was settled. Each pair of debit/credit transactions has their own Settle Id and is listed in the Settle Id column. The second credit transaction for 400.00 is not fully settled so the status is Partially settled and the remaining amount is updated to 100.00.

 table 2

 ## View settlements/Ledger settlements history

To view the Settle Id and history of settlements select a transaction with a Settle Id and then View settlements in the action bar. The Ledger settlement history page shows each pair of debit and credit transactions settled using the Settlement ID created for each pair. 

Use the Ledger settlement history page to reverse any transactions that are already settled. Select a transaction and the corresponding transaction with the same Settlement ID will be selected automatically. Select Reverse marked transactions, choose the reversal date options and enter a comment if needed. Then select Reverse. If a transaction has been settled and then reversed and has a status of partially settled or Not settled, the History column has a checkmark to show there is history. Select View settlements to view all settlement history. Select the Show reversals checkbox to see all reversed settlements. 

The User ID column provides an audit trail of the user ID that did the settlement or the reversal transaction.

## Ledger settlements inquiry

Use the Ledger settlements inquiry page, found under General ledger > Inquiries and reports > Ledger settlements inquiry, to view ledger settled transactions. The columns Remaining amount in transaction currency, Remaining amount in accounting currency, and Remaining amount in reporting currency have been added to the grid and display values with partially settled transactions. 

If the Settlement ID column displays Multiple, select the View settlements button to go to the Ledger settlement history page to view full settlement history. 

## Subledger to ledger auto settlement

The Subledger to ledger auto settlement option is found in General Ledger > Ledger setup > General ledger parameters > Ledger settlements. To enable it the following options need to be set to Yes: Enable advanced awareness options, Enable post currency realized gains and losses for ledger settlements, and Partial ledger settlements. The Subledger to ledger auto settlement can be toggled on (Yes) and off (No) when needed. 

When set to Yes, the Subledger to ledger auto settlement will automatically settle the accounts payable and accounts receivable accounts during the settlement process in the subledger. This option needs to be set to Yes to automatically settle but the accounts receivable and accounts payable accounts do not need to be manually added to the list of accounts. If the accounts are added to the list of accounts, then they can be viewed in the Ledger settlements page. Transactions that are automatically settled can then be viewed. If needed, you can manually settle any transactions that use the accounts payable or accounts receivable accounts. 

Adding other subledger accounts to the list of accounts will not automatically settle those accounts. If added, then those subledger accounts can be manually settled in Ledger settlements. 

Existing transactions in the accounts payable and accounts receivable accounts will not be automatically settled if the related subledger transactions were settled before setting this option to Yes.



