---
title: Create budget register entries
description: This article describes how to create budget register entries.
author: twheeloc
ms.author: twheeloc
ms.topic: overview
ms.date: 05/30/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: global
ms.search.validFrom: 2016-02-28
ms.search.form: BudgetParameters
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 28a9793e-d376-47af-a345-69046bad17df
---

# Create budget register entries

[!include [banner](../includes/banner.md)]

This article describes how to create budget register entries.

Before you can create budget amounts by entering budget register entries, you must define financial dimensions for Budgeting. You must also set up budget codes, budget models, exchange rates, and number sequences.

If you plan to use budgeting workflows, create the workflows, and then assign them to budget codes. If you plan to use budget control, configure it before you enter budget amounts.

## Create a budget register entry

> [!NOTE]
> The **Budget register entries performance enhancement** feature provides additional performance gain on the **Budget register entries** page by splitting the entries into two separate pages: one for **Completed** status and one for **Draft** status. There are major performance gains on the **Draft entries** list. This feature can be enabled in Feature management.
 
To create a budget register entry, follow these steps.

1. Go to **Budgeting** \> **Budget register entry** to create a budget register entry.
1. On the **Budget register entry** FastTab, select a budget model and a budget code. The reason code is optional. 

    > [!NOTE]
    > If a workflow is activated for the selected budget code, the budget register entry is submitted to that workflow.

1. If posting definitions are enabled, select and hold (or right-click) the **Posting definition** field, and then select **View details** to verify the posting definition. The posting definition that is shown is the posting definition that is selected for the budget type or budget code on the **Transaction posting definitions** page.
1. In the **Budget account entries** grid, select **Add line**.
1. Enter a date. This date determines the period that the budget is recorded to.
1. Select an account structure.
1. Enter the financial dimension values.
1. Enter the budget amount and the budget amount type.
1. Select a currency.
1. On the Action Pane, select **Update budget balances**.
1. Select **OK**, or enter batch criteria.
 
## Create a budget transfer

You can create budget transfers by creating a budget register entry that has a budget code that is associated with the **Transfer budget** type. Decrease the budget of one or more financial dimension values, and then increase the budget of other financial dimension values by the same amount.

1. Select **Budgeting** \> **Budget register entry** to create a budget register entry.
1. On the **Budget register entry** FastTab, select a budget model and a budget code that is associated with the **Transfer budget** type.
1. In the **Budget account entries** grid, select **Add line**. Enter the account structure and financial dimension values to transfer a budget amount from. Then enter a negative amount, such as **-1000.00**.
1. Select **Add line** to add a line for the account structure and financial dimension values that you want to transfer the budget amount to. Then enter a positive amount, such as **1000.00**.

    If multiple accounts must be used to increase the budget of the financial dimension values that are receiving the budget amount, add lines, and then enter a negative amount on each line.

1. Select **Update budget balances**.

    If a workflow is activated for the selected budget code for the budget transfer, the budget transfer request is submitted to that workflow.

1. If a workflow isn't activated, select **OK**, or enter batch criteria.

## Allocate budget register entries

You can allocate budget register entries across periods or to financial dimensions.
Period allocation keys define the percentage of a budget register entry that is allocated to specific periods. Period allocation keys work with the fiscal year definition for the fiscal calendar that is associated with the ledger. For example, if the fiscal year starts on July 1 and ends on June 30, and the period allocation is **Fixed**, the allocation is applied from the current date through June 30. 

Budget allocation terms define the percentage of a budget register entry that is allocated to specific financial dimension values. For example, a percentage of the travel budget can be allocated to various departments.

1. Go to **Budgeting** \> **Budget register entry** to create a budget register entry.
1. On the **Budget register entry** FastTab, select a budget model and a budget code.
1. In the **Budget account entries** grid, select **Add line**. Enter the date, account structure, financial dimension values, amount, and amount type.
1. Save the line.
1. Follow one of these steps:

    - To allocate across periods, select **Allocate across periods**, select a period allocation key, and then select **Allocate**.
    - To allocate to financial dimensions, select **Allocate to dimensions**, select a budget allocation term, and then select **Allocate**.

1. In the **Budget account entries** grid, verify the new lines. A reversal entry is created for the budget account that you specified, and new budget account entries are created based on the allocation that you selected.
1. Select **Update budget balances**.
1. Select **OK**, or enter batch criteria.
