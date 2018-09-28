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
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom:
# ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: mikefalkner
ms.search.validFrom: 2018-11-30
ms.dyn365.ops.version: 8.1.1

---

# Ledger settlements

[!include [banner](../includes/banner.md)]

Ledger settlements lets you match debit and credit transactions in the general ledger and mark them as settled. In this way, you can make sure that related transactions have been cleared. You can also reverse settlements if they were made by mistake.

## Enabling advanced ledger settlements

The advanced ledger settlements form provides additional capabilities for selecting transactions and filtering them. To enable advanced ledger settlements:

1. Select **General ledger** \> **Ledger setup** \> **General ledger parameters**. 
2. Click on the tab called **Ledger settlements**. 
3. Select Yes for **Advanced ledger settlement**. This will enable the advanced ledger settlement functionality.
4. You must enter a list of accounts that you want to use for ledger settlements for each chart of accounts. Select a chart of accounts from the **Chart of accounts** list. 
5. Use the **New** menu to add new accounts to the list. This list will be used to filter the list of transactions that will be shown in the ledger settlements form.

## Settle transactions using advanced ledger settlements

To settle ledger transactions, follow these steps.

1. Select **General ledger** \> **Periodic** \> **Ledger settlements**. 
2. You will see several filters at the top of the page. 
- Select a date range or use the **Date interval code** to automatically populate the date range
- Change the **Posting layer** if needed.
- If you want to display the ledger account and dimensions separately, select a **Financial dimension set**.
3. Click on the **Display transactions** button to show all of the transactions that match the filters and match the list of accounts that you specified during the setup of the chart of accounts list. If you change any of the filters or the dimension sets, you must click on the **Display transactions** button again. 
4. Select one or more lines that you're considering for settlement. The value of the **Selected amount** field at the top of the page increases or decreases by the total amount on the lines that you selected.
5. After you've finished selecting transactions, select **Mark selected**. A check mark appears in the **Marked** column for each of those transactions. Additionally, the value of the **Marked amount** field above the grid will increase or decrease by the total amount on the lines that you marked.
6. When the **Marked amount** value is 0 (zero), select **Settle marked transactions**. The status of the marked transactions is updated to **Settled**.

## Make transactions easier to find

The **Ledger settlements** page includes capabilities that make it easier to display the transactions that you need for settlement.

- The **Unmark selected** button clears the **Marked** column for all lines that are selected.
- The **Marked** filter lets you filter transactions based on whether the **Marked** column for them is selected or cleared.
- The **Status** filter lets you filter transactions based on whether their status is **Settled** or **Not settled**.
- The **Sort by absolute amount** button lets you sort the amounts by absolute value, so that you can group together debits and credits that have the same amount.

## Reverse a settlement

You can reverse a settlement that was made by mistake.

1. Follow the steps described above to display the transactions that you are looking for.
2. In the **Status** drop-down filter, select **Settled**.
3. Select one or more lines that you're considering for reversal. The value of the **Selected amount** field at the top of the page increases or decreases by the total amount on the lines that you selected.
4. After you've finished selecting transactions, select **Mark selected**. A check mark appears in the **Marked** column for each of those transactions. Additionally, the value of the **Marked amount** field at the top of the page increases or decreases by the total amount on the lines that you marked.
5. When the **Marked amount** value is 0 (zero), select **Reverse marked transactions**. The status of the marked transactions is updated to **Unsettled**.

## Update the list of accounts that will be included in the list of transactions

You can use the **Ledger settlement accounts** menu to open a form that allows you to edit the accounts that will be included in the list of transactions. This is the same form that is used when you click on the **Ledger settlements** tab in the **General ledger parameters**. 

Use the **New** menu to add new accounts to the list. This list will be used to filter the list of transactions that will be shown in the ledger settlements form.
