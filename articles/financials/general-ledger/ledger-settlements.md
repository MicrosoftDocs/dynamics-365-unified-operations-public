---
# required metadata

title: Ledger settlements
description: This topic explains how to use the Ledger settlements page to settle ledger transactions and reverse settlements.
author: mikefalkner
manager: aolson
ms.date: 08/24/2018
ms.topic: index-page
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

Ledger settlements let you match debit and credit transactions in the general ledger. In this way, you can make sure that related transactions have been cleared. You can also reverse settlements if they were made by mistake.

## Settle transactions

To settle ledger transactions, follow these steps.

1. Select **General ledger** \> **Periodic** \> **Ledger settlements**. You see a list of all the unsettled transactions in the general ledger. They all have a status of **Not settled**.
2. Select one or more lines that you're considering for settlement. The value of the **Selected amount** field at the top of the page increases or decreases by the total amount on the lines that you selected.
3. After you've finished selecting transactions, select **Mark selected**. A check mark appears in the **Marked** check box for each of those transactions. Additionally, the value of the **Marked amount** field at the top of the page increases or decreases by the total amount on the lines that you marked.

    > [NOTE!]
    > You can also directly mark a transaction for settlement by selecting the **Mark** check box for it. In a future release, a rules engine will be added that will mark transactions based on column values that you specify.

4. When the **Marked amount** value is 0 (zero), select **Settle marked transactions**. The status of the marked transactions is updated to **Settled**.

## Reverse a settlement

You can reverse a settlement that was made by mistake.

1. Select **General ledger** \> **Periodic** \> **Ledger settlements**. You see a list of all the unsettled transactions in the general ledger.
2. In the **Status** drop-down filter, select **Settled**.
3. Select one or more lines that you're considering for reversal. The value of the **Selected amount** field at the top of the page increases or decreases by the total amount on the lines that you selected.
4. After you've finished selecting transactions, select **Mark selected**. A check mark appears in the **Marked** check box for each of those transactions. Additionally, the value of the **Marked amount** field at the top of the page increases or decreases by the total amount on the lines that you marked.

    > [!NOTE]
    > You can also directly mark a transaction for reversal by selecting the **Mark** check box for it.

5. When the **Marked amount** value is 0 (zero), select **Reverse marked transactions**. The status of the marked transactions is updated to **Unsettled**.

## Make transactions easier to find

The **Ledger settlements** page includes capabilities that make it easier to find information:

- The **Mark selected** button selects the **Marked** check box for all lines that are selected.
- The **Unmark selected** button clears the **Marked** check box for all lines that are selected.
- The **Marked** filter lets you filter transactions based on whether the **Marked** check box for them is selected or cleared.
- The **Status** filter lets you filter transactions based on whether their status is **Settled** or **Not settled**.
- The **Sort by absolute amount** button lets you sort the amounts by absolute value, so that you can group together debits and credits that have the same amount.
- The **Posting layer** filter lets you filter transactions based on the posting layer.
- The **Financial dimension set** field lets you add the financial dimensions as a column, so that you can filter on each dimension.

Additionally, notice that the lower part of the page includes a grid that resembles the grid in the upper part of the page. This lower grid lets you search for different combinations of transactions without changing the filters and settings that you're using in the upper grid. You can select and mark transactions in both grids. You can also use the ellipsis button (**...**) to reduce the size of the lower grid so that you have more room to view the upper grid.
