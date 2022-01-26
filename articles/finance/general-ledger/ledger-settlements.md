---
# required metadata

title: Ledger settlements
description: This topic explains how to use the Ledger settlements page to settle ledger transactions and reverse settlements.
author: kweekley
ms.date: 09/28/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  LedgerTransSettlement
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom:
# ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-11-30
ms.dyn365.ops.version: 8.1.1

---

# Ledger settlements

[!include [banner](../includes/banner.md)]

Ledger settlements is the process of matching debit and credit transactions in the general ledger.  The settlement of the debit and credit amount is used as a tool for reconciling the balance of the ledger account to the detailed transactions that comprise the balance.  Settled transactions can be excluded from inquires and reports, making it easier to analyze the open ledger transactions that comprise the balance of the ledger account. 

> [!IMPORTANT]
> The accounts payable (AP) and accounts receivable (AR) modules also have settlement of invoices and payments.  When the settlement occurs in the AR and AP subledgers, the corresponding ledger entries are not automatically settled.  

## Ledger settlement features

As of application release 10.0.21, the General ledger parameter “Enable advanced ledger settlement” was removed to enable Advanced ledger settlement and is now always enabled. 

As of application release 10.0.25, a new feature “Awareness between ledger settlement and year-end close” was introduced that changes fundamental functionality in both ledger settlement and General ledger year-end close.  Before enabling the feature in Feature management, please read the following documentation . 

## Set up ledger settlement
When using ledger settlement, first select the main accounts for which ledger settlement is performed.  This can done through the following:

- Go to General ledger > Ledger setup > General ledger parameters.  Choose Ledger settlements from the Table of contents.  

    - Select the Charts of accounts from which you will select the main account.  
    - Select the main accounts for which you will perform ledger settlement. Because the Charts of accounts are global, all companies assigned the selected chart of accounts will have the same main accounts selected for ledger settlement.

- Go to General ledger > Periodic tasks > Ledger settlements. Select the Ledger settlement accounts button. In the dialog, select the Charts of accounts and Main accounts for which you will perform ledger settlement.  This dialog is a short cut, so any main accounts added here will also be reflected in General ledger parameters.

Main accounts can be removed from ledger settlement using the same two pages.  Main accounts can be removed at any time.  Removing a main account has no effect on previous ledger settlements, but you will no longer see that main account or transactions on the Ledger settlement page.

## Settle transactions 

To settle ledger transactions, follow these steps.

1.	Select General ledger > Periodic tasks > Ledger settlements.
2.	Set the filters at the top of the page:

    1. Select a date range or Date interval code to automatically fill in the date range.  It is not recommended to ledger settle transactions that cross fiscal years. 
    2. Change the posting layer as you require.  It is not permitted to settle transactions in different posting layers. 
    3. To show the main account and dimensions separately, select a financial dimension set.

3.	Select Display transactions to show all the transactions that match the filters that you set and the list of accounts that you specified when you set up the chart of accounts list in the previous section. 

    - If you change any of the filters or the dimension sets, you must select Display transactions again.
    - Use the filter on the Ledger account to filter the transactions to an individual main account.  It is not recommended to ledger settle transactions posted to different main accounts. 

4.	Select one or more lines that you're considering for settlement. The value of the Selected amount field at the top of the page increases or decreases by the total amount on the lines that you selected.
5.	After you've finished selecting transactions, select Mark selected. A check mark appears in the Marked column for each transaction that you selected. Additionally, the value of the Marked amount field above the grid increases or decreases by the total amount on the lines that you marked.
6.	When the Marked amount value is 0 (zero), select Settle marked transactions. The status of the marked transactions is updated to Settled.

    > [!NOTE]
    > All transactions marked for settlement by the user for the active legal entity will be settled, even if they are not shown on the screen.  This can happen if a filter is applied.  

## Make transactions easier to find

The **Ledger settlements** page includes capabilities that make it easier to see the transactions that you need for settlement.

- The Marked filter lets you filter transactions based on whether the Marked field for them is selected or cleared.
- The Status filter lets you filter transactions based on whether their status is Settled or Not settled.
- The Sort by absolute amount button lets you sort the amounts by absolute value, so that you can group together debits and credits that have the same amount.

## Reverse a settlement

1. Follow steps 1 through 3 in the "Settle transactions” section to show the transactions that you're looking for.
2. In the Status filter, select Settled.
3. Select one or more lines that you're considering for reversal. 
4. Select Reverse marked transactions. The status of all transactions with the same Settlement ID is updated to Not settled.

    > [!IMPORTANT]
    > All transactions with the same Settlement ID will be reversed, even if they are not marked. For example, four lines were marked and settled. They all have the same Settlement ID.  The user marks one of the four lines and chooses to reverse, all four lines will be reversed.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
