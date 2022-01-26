---
# required metadata

title: Awareness between ledger settlement and year-end close
description: This topic provides information about enhancements which impact ledger settlements and the General ledger year-end close.
author: kweekley
ms.date: 01/26/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
# ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2022-01-31
ms.dyn365.ops.version: 10.0.25

---

# Ledger settlements

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

As of Dynamics 365 Finance application release 10.0.25, a new feature, **Awareness between ledger settlement and year-end close** is available in **Feature management**. The feature adds two primary enhancements which impact Ledger settlement and the General ledger year-end close. 

First, during the General ledger year-end close, ledger transactions that are settled will no longer be included in the opening balance of the next fiscal year. This functionality ensures that only ledger transactions not settled are included in the opening balance, which is important when running the General ledger foreign currency revaluation.  Foreign currency revaluation is only run for ledger transactions in a state of **Not settled**. Before this feature the opening balance summarized both **Settled** and **Not settled** transactions, with the summarized amount set to **Not settled**.

The second enhancement gives you the option to post detailed opening balance transactions during the General ledger year-end close. If **Keep detail during year-end close** is **Yes**, a separate opening balance will be created for each ledger transaction that is not settled. This setting is defined per main account in Ledger settlement setup. Keeping detailed transactions for the opening balance greatly improves the ability to settle the unsettled ledger transactions in the next fiscal year.    

To support the new enhancements, changes were made to ledger settlement and the year-end close.  

**Ledger settlement**
- Ledger settlement must be done within a fiscal year.
- Ledger settlement must be done for transactions within a single main account.

   - The main account is now a required filter on the Ledger settlement page  . 

- Ledger settlement and reversal of ledger settlement cannot be done for transactions with a closed fiscal year (year-end close has been run).

**Year-end close**
- A year-end close cannot be reversed if any opening balance transactions have been settled in the next fiscal year.  This includes reversing the year-end close or rerunning the year-end close with the General ledger parameter **Delete existing year-end entries when re-closing the year** set to **Yes**. 
- If any balance sheet account is marked in the Ledger settlement as **Keep detail during year-end close** set to **Yes**, more detailed opening balance transactions will be created for that main account.  

## Before you enable the feature  
With the functional and data model changes, it’s important to consider the following before enabling this feature:

- All transactions ‘Marked’ for settlement, but not settled, will be unmarked automatically when the feature is enabled. To prevent any lose of work, all marked transactions should be settled before the feature is enabled. 
- Some organizations run the year-end close multiple times for the same fiscal year. The feature must not be enabled if the year-end close has been run once but will be run again for the same fiscal year. The feature must be enabled before processing the first year-end close or after processing the last year-end close for the fiscal year. 

   - If the year-end close has been run once but you want to enable the feature, reverse the year-end close and then the feature can be enabled.

- Because settlement across fiscal years is no longer permitted, we recommend enabling the feature before beginning the year-end close process.  Also, the opening balance transaction should be settled for the fiscal year being closed.  This is to ensure that the next fiscal year’s opening balances are not impacted by previous cross-fiscal year settlements.
- Because settlement across main accounts is no longer permitted, you may need to adjust your chart of accounts or processes to ensure ledger settlement can be done within the same main account. 
- This feature cannot be enabled if the public sector year-end close is being used.  

## Set up ledger settlement
After enabling the feature and before running the next year-end close, each organization must determine whether they will choose to keep the transaction detail during the year-end close.  This option has no impact on opening balance postings from previous year-end close processes. 
The option **Keep detail during year-end close** is defined per main account on the **Ledger settlement setup** page.  Go to **General ledger** > **Ledger setup** > **General ledger parameters**.  Choose **Ledger settlements** from the Table of contents.  The same setup can also be found under **General ledger** > **Periodic tasks** > **Ledger settlements**.   Select the **Ledger settlement accounts** button. 
Two columns have been added.  First, the **Main account type** assigned to the main account is displayed and is for informational purposes only.  The **Keep detail during year-end close** column defaults to **No** and can only be changed to **Yes** if the **Main account type** for the main account is **Balance sheet**, **Asset**, or **Liability**.  
If this setting remains at **No**, the opening balances will be posted in summary as normally done during the year-end close.  If this setting is changed to **Yes**, the opening balances will be created in detail for each ledger transaction that is not settled for the main account. 

## Year-end close
When running the year-end close under **General ledger** > **Period close** > **Year end close**, the process will create the opening balances for the main accounts defined for ledger settlement in either summary or detail, dependent on the setup in Ledger settlement. It will also exclude ledger transactions that are settled, whether you choose to post the opening balance in summary or detail for each main account.
Assume the following transactions are posted to main account **130100** in fiscal year 2021.
 
Of these transactions, three are settled within Ledger settlement.  Note that the USD invoice for $175 was paid by a EUR payment, and a cash discount was taken. 
 

Let’s look at what happens for main account 130100 when running the year-end close before the feature is enabled vs after enabling the feature.  Also, we’ll see the difference when **Keep detail during year-end close** is either **No** and **Yes**. 

### Feature is not enabled
The year-end close creates the following opening balances in 2022 for main account 130100. The sum of the transactions in the accounting currency is $525 USD.
 
Even though the payment’s transaction for -127.11 EUR was ledger settled, it still comes forward as a beginning balance. 
Feature is enabled and **Keep detail during year-end close** = **No**.
The year-end close creates the following opening balances in 2022 for main account 130100. The sum of the transactions in the accounting currency is still $525 USD but the ledger settled transactions were excluded from the opening balance. The total amount for 130100-002- is $125 instead of $299.12 and the 127.11 EUR/174.12 USD transaction is excluded completely. 
 
### Feature is enabled 
When the features is enabled, and **Keep details during year-end-close** is set to **Yes**, the year-end close creates the following opening balances in 2022 for main account 130100. A separate opening balance transaction is created for each of the five transactions that weren’t settled. The sum of the transactions in the accounting currency is still $525.
 
When keeping transaction details, the original detailed transactions are not impacted.  They remain posted and they remain unsettled in the fiscal year being closed.  A copy of those transactions is created for the opening balance. The following values from the original transactions will be copied to the opening balance transactions:  

- Ledger account – Main account and all financial dimensions
- Transaction, accounting, and reporting currency amounts 
- Description
- Posting layer
- Posting type

  - Note that all other opening balance transactions are NOT assigned a posting type, so this is one way to differentiate opening transactions that were brought forward in detail.

Some fields from the original transactions must change on the opening balance detailed transactions. The Date of opening balance transactions is always the first day of the next fiscal year.  The Journal number must change and the voucher number changes to the value entered on the year-end close dialog.

Information from the original transactions can be found on the Ledger settlement page.  Each detailed opening balance transaction will show the Original transaction date as a column within the grid, which will be helpful when matching transactions in the new fiscal year.  Also, the View original voucher button is available for the user to drill back to the full original voucher.

## Settle transactions 
To settle ledger transactions, go to General ledger > Periodic tasks > Ledger settlements.  

1. Set the filters at the top of the page:

   1. Select a date range or Date interval code to automatically fill in the date range.  

      - The date range cannot cross fiscal years.  If the date range crosses fiscal years, no transactions will be shown when selecting Display transactions.  
      - If the date range is within an open fiscal year, transactions can be settled and settlement can be reversed.  If the date range is within a closed fiscal year (year-end close completed), transactions will be shown but can’t be settled or unsettled.  You can only unmark transactions in a closed fiscal year. The Mark selected, Settle marked transactions, and Reverse marked transactions button are disabled when the date range is within a closed fiscal year. 

   2.	Select the Main account for which transactions to display.  This is a required field.  The lookup will only display main accounts selected in the Ledger settlement page for this company’s chart of accounts.
   3.	Select the Posting layer.  It is not permitted to settle transactions in different posting layers. 
   4.	To show the main account and dimensions in separate columns, select a Financial dimension set.

2. Select **Display transactions** to show all the transactions that match the filters that you set. If you change any of the filters or the dimension sets, you must select **Display transactions** again.
3. Select one or more lines that you're considering for settlement. The value of the **Selected amount** field at the top of the page increases or decreases by the total amount on the lines that you selected.
4. After you've finished selecting transactions, select **Mark selected**. A check mark appears in the **Marked** column for each transaction that you selected. Additionally, the value of the **Marked amount** field above the grid increases or decreases by the total amount on the lines that you marked.
11.	When the **Marked amount value** is 0 (zero), select **Settle marked transactions**.  Partial settlement is not permitted.  For example, you cannot settle a $100 debit transaction against a $90 credit transaction. The remaining $10 credit transaction must also be marked for inclusion in the settlement.
13.	Enter a Settlement date. The date must be on or after the latest date of the transactions marked for settlement. The status of the marked transactions is updated to **Settled**.

  > [!NOTE]
  > All transactions marked for settlement by the user, for the active legal entity, and for the selected main account, will be settled.  The transactions do not need to appear on the screen; they will be settled even if they are hidden as the result of a filter.   

There are some processes, such as reversing a transaction, that will automatically settle ledger transactions.  Let’s say a payment and invoice are settled in Accounts receivable, and the settlement generated a realized gain/loss.  The settlement of the payment and invoice does NOT settle any ledger transactions, such as for the accounts receivable ledger account.  But let’s say that the payment and invoice are unsettled in Accounts receivable.  The reversing accounting entry that was posted during the reversal of the AR settlement will cause the original and reversing accounting entries to be ledger settled within General ledger.  When this feature is enabled, the ledger settlement of a reversal will not occur automatically if the reversing date is in a different fiscal year. 

## Using Microsoft Excel for ledger settlement
Transactions displayed on the Ledger settlement page can be exported to Excel.  Excel can be used to further filter transactions when determining which transactions to mark for settlement.  

Both Ledger settlement entities will only export ledger transactions for the main account selected on the page.  Also, transactions for closed fiscal years can still be marked or unmarked using Excel, but they cannot be settled and the reversal of settled transactions cannot be done for that fiscal year. 

## Make transactions easier to find
The **Ledger settlements** page includes capabilities that make it easier to see the transactions that you need for settlement.

- The Marked filter lets you filter transactions based on whether the Marked field for them is selected or cleared.
- The Status filter lets you filter transactions based on whether their status is Settled or Not settled.
- The Sort by absolute amount button lets you sort the amounts by absolute value, so that you can group together debits and credits that have the same amount.

## Reverse a settlement  
You can reverse a settlement that was made by mistake.
1. Follow steps 1 through 3 in the "Settle transactions” section to show the transactions that you're looking for.
2. In the Status filter, select Settled.
3. Select one or more lines that you're considering for reversal. 
4. Select Reverse marked transactions. The status of all transactions with the same Settlement ID is updated to Not settled.

  > [!NOTE]
  > All transactions with the same Settlement ID will be reversed, even if they are not marked. For example, four lines were marked and settled so they all have the same Settlement ID.  The user marks one of the four lines and chooses to reverse.  All four lines will be reversed.
