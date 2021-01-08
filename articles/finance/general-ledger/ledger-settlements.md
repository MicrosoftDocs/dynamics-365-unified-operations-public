---
# required metadata

title: Ledger settlements
description: This topic explains how to use the Ledger settlements page to settle ledger transactions and reverse settlements.
author: mikefalkner
manager: aolson
ms.date: 09/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  LedgerTransSettlement
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
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

Ledger settlements let you match debit and credit transactions in the general ledger, and mark them as settled. In this way, you can make sure that related transactions have been cleared. You can also reverse settlements if they were made by mistake.

## Enable advanced ledger settlements

The advanced ledger settlements page provides additional capabilities for filtering and selecting transactions. To enable advanced ledger settlements page, follow these steps.

1. Select **General ledger** \> **Ledger setup** \> **General ledger parameters**. 
2. On the **Ledger settlements** tab, set the **Advanced ledger settlement** option to **Yes** to turn on the advanced ledger settlement functionality. The advanced **Ledger settlements** page will be used when you select **Ledger settlements** in the **Periodic tasks**. 
3. You must enter the list of accounts to use for ledger settlements for each chart of accounts. This list is used to filter the list of transactions that appears on the **Ledger settlements** page. In the **Chart of accounts** list, select a chart of accounts, and then select **New** to add new accounts to the list.

## Settle transactions by using the advanced ledger settlements page

To settle ledger transactions, follow these steps.

1. Select **General ledger** \> **Periodic tasks** \> **Ledger settlements**.
2. Set the filters at the top of the page:

    - Select a date range, or select **Date interval code** to automatically fill in the date range.
    - Change the posting layer as you require.
    - To show the ledger account and dimensions separately, select a financial dimension set.

3. Select **Display transactions** to show all the transactions that match the filters that you set and the list of accounts that you specified when you set up the chart of accounts list in the previous section. If you change any of the filters or the dimension sets, you must select **Display transactions** again.
4. Select one or more lines that you're considering for settlement. The value of the **Selected amount** field at the top of the page increases or decreases by the total amount on the lines that you selected.
5. After you've finished selecting transactions, select **Mark selected**. A check mark appears in the **Marked** column for each transaction that you selected. Additionally, the value of the **Marked amount** field above the grid increases or decreases by the total amount on the lines that you marked.
6. When the **Marked amount** value is **0** (zero), select **Settle marked transactions**. The status of the marked transactions is updated to **Settled**.

## Make transactions easier to find

The **Ledger settlements** page includes capabilities that make it easier to see the transactions that you need for settlement.

- The **Unmark selected** button clears the **Marked** field for all lines that are selected.
- The **Marked** filter lets you filter transactions based on whether the **Marked** field for them is selected or cleared.
- The **Status** filter lets you filter transactions based on whether their status is **Settled** or **Not settled**.
- The **Sort by absolute amount** button lets you sort the amounts by absolute value, so that you can group together debits and credits that have the same amount.

## Reverse a settlement

You can reverse a settlement that was made by mistake.

1. Follow steps 1 through 3 in the "Settle transactions by using advanced ledger settlements page" section to show the transactions that you're looking for.
2. In the **Status** filter, select **Settled**.
3. Select one or more lines that you're considering for reversal. The value of the **Selected amount** field at the top of the page increases or decreases by the total amount on the lines that you selected.
4. After you've finished selecting transactions, select **Mark selected**. A check mark appears in the **Marked** column for each transaction that you selected. Additionally, the value of the **Marked amount** field at the top of the page increases or decreases by the total amount on the lines that you marked.
5. When the **Marked amount** value is **0** (zero), select **Reverse marked transactions**. The status of the marked transactions is updated to **Not settled**.

## Update the list of accounts that are included in the list of transactions

Select **Ledger settlement accounts** to open a dialog box where you can edit the accounts that are included in the list of transactions. Select **New** to add new accounts to the list. This list is used to filter the list of transactions that appears on the **Ledger settlements** page.
