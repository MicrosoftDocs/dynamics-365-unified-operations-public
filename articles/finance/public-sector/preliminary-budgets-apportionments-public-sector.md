---
title: Preliminary budgets and apportionments in the public sector
description: This article covers creating a preliminary budget, and setting up budgeting and budget control for apportionments and a preliminary budget.
author: velofog
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: velofog
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 8885478d-67f5-4db8-b97b-c0734216f8dd
ms.search.industry: Public sector
ms.search.form: BudgetBalancesActuals, BudgetControlConfiguration, BudgetTransactionCode
---

# Preliminary budgets and apportionments in the public sector

[!include [banner](../includes/banner.md)]

This article covers creating a preliminary budget, and setting up budgeting and budget control for apportionments and a preliminary budget. 

The following sections in this article describe the budgeting features that are available for the public sector.  Before you read this article, you should also read [Budgeting in the public sector](budgeting-public-sector.md).

-   Setting up budgeting and budget control for apportionments - You can define one or more budget codes for the apportionment budget type and configure budget control for apportionments.
-   Setting up budgeting and budget control for a preliminary budget - You can define budget codes for the preliminary budget type and configure budget control for preliminary budgets.
-   Creating, viewing, and reversing a preliminary budget - You can create preliminary budget entries, as well as create original budget entries.


## Set up budgeting and budget control for apportionments
Apportionments are the portion of the original budget that has been approved for spending. For example, an organization might have an original budget of $1,000,000 but only have authority to spend $150,000 in the first quarter of the fiscal year. You could record an original budget register entry for $1,000,000 for the fiscal year. Then you could record an apportionment budget register entry for $150,000 for the first three months of the year. Only the $150,000 that was apportioned could be spent during the first quarter. 

> [!NOTE] 
> You cannot apportion more than the original budget amount for the financial dimension values. 

After you set up basic budgeting and budget control, use the following to add information about apportionments to basic budgeting and budget control.

### How do I define budget codes for the apportionment budget type?

You can define one or more budget codes for the apportionment budget type on the **Budget codes** page. You should define the budget codes for the original budget type during the setup for basic budgeting. When you create a new budget code and description, also select the apportionment budget type.

Use budget codes for the apportionment budget type when you enter budget register entries for the apportioned budget amounts. Use budget codes for the original budget type when you enter budget register entries for the original budget amounts.

### How do I configure budget control for apportionments?

The **Budget control configuration** page contains options for working with apportionments. 

In the **Budget funds available** section, when you select the **Use only apportioned amount** option, the other options under **Amounts to sum** become unavailable. Also, the budget funds available calculation includes only apportioned amounts in the amounts to sum. Typically, you would include actual expenditures, budget reservations for encumbrances, budget reservations for unconfirmed encumbrances, and budget reservations for pre-encumbrances in the amounts to subtract. 

> [!NOTE] 
> When **Use only apportioned amount** is selected, the original budget, transfers, and revisions are still tracked but not used in the calculation. 

In the **Documents and journals** section, when you select **Purchase requisitions**, note that the options for purchase orders and vendor invoices are automatically selected. 

After you define budget codes for basic budgeting and configure budget control for apportionments, you can create budget register entries for the original budget and apportionment budget types. For more information, see "How do I create and view a preliminary budget?" later in this article.

### Tips

On the **Budget register entries** page, you can track and audit budget activities for apportionments by viewing:

-   Budget balances
-   Budget control statistics
-   Actual versus budget totals
-   Budget register entries that include original budget and apportionments

You can also track and audit budget activities for apportionments from the following pages:

-   The **Period budgets** page displays budget and apportionment balances by period, accumulated amounts, and the accumulated percentage of the sum of the budget and apportionments for all periods.
-   The **Budget control statistics** page displays the budget balances for a budget cycle and budget model. To see additional details, select a line in the grid, and then click **Apportionments**. After purchase requisitions and purchase orders have been posted, you can use the **Budget control statistics** page to view the budget reservations for encumbrances and pre-encumbrances. **Note:** The **Apportionments** and **Preliminary budget** fields appear only if you have selected **Preliminary budget** and **Use only apportioned amount** in the **Budget funds available** section of the **Budget control configuration** page.
-   The **Actual vs. budget by period** page displays actual expenditures versus the sum for the budget register entries for the period:
    -   The **Apportionments** field contains a sum of all the apportionment budget register entries for the budget model and dimension values.
    -   The **Variance amount** column displays the result of the following calculation: Apportionment for the period – Actual for the period = Variance amount for the period.
    -   The **Preliminary budget** field contains a sum of all the preliminary budget register entries for the budget model and dimension values.

## Set up budgeting and budget control for a preliminary budget
After you set up basic budgeting and budget control, use the following to add information about preliminary budgets to basic budgeting and budget control. 

You can create a temporary, preliminary budget while the actual budget is being reviewed and approved. If you use budget control, you can select source documents and accounting journals to evaluate for budget control while you use the preliminary budget. You can track the preliminary budget amounts by using separate budget codes for the preliminary budget type, and then, after the approved budget is adopted, the preliminary budget amounts can be reduced as the approved budget amounts are increased.

### How do I define budget codes for the preliminary budget type?

You can define budget codes for the preliminary budget type on the **Budget codes** page. If you want to track different categories of preliminary budget register entries, you can define multiple budget codes for the preliminary budget type. 

You should define the budget codes for the original budget type during the setup for basic budgeting. When you create a budget code and description, also select the preliminary budget type. 

Use budget codes for the preliminary budget type when you enter budget register entries for the preliminary budget amounts. Use budget codes for the original budget type when you enter budget register entries for the original budget amounts.

### How do I configure budget control for preliminary budgets?

The **Budget control configuration** page contains the options for working with preliminary budgets. In the **Budget funds available** section, select the **Preliminary budget** option. Note that you may need to click **Create draft** to proceed. 

> [!NOTE]
> If preliminary budgets are included in the budget funds available calculation, it is important to reverse the preliminary budget register entries when the original budget register entries are recorded in the budget balances. If the budget register entries with preliminary budget codes are not reversed, then both the preliminary budget and original budget types are added, which will overstate the available balance. For more information, see "How do I reverse a preliminary budget?" later in this article. In the **Documents and journals** section, when you select the **Purchase requisitions** option, note that the options for purchase orders and vendor invoices options are automatically selected.


## Create, view, and reverse a preliminary budget
After you set up basic budgeting and budget control for the preliminary budget, you can create budget register entries for the preliminary budget type.

### How do I create and view a preliminary budget?

You can create preliminary budget register entries for a specific budget model and dimension values. After the actual budget is approved, you can create original budget register entries.

#### Tips

To view additional information about preliminary budgets, select the following inquiries:

-   Use the **Budget control statistics** page to view the budget balances for a budget cycle and budget model. After purchase requisitions and purchase orders have been posted, you can view the budget reservations for encumbrances and pre-encumbrances.
-   Use the **Actual vs. budget** page to view actual expenditures versus the sum for the budget register entries for the period. The **Preliminary budget** field contains a sum of all the preliminary budget register entries for the budget model and dimensions values.

### How do I reverse a preliminary budget?

When you create an original budget entry and use the budget model and dimension values that contain preliminary budget amounts, the preliminary budget amounts can be reversed. For example, you could enter a preliminary budget amount of $2,500 in ledger account 50000. Later, if you enter an original budget amount of $10,000 in ledger account 50000, the preliminary budget amount of $2,500 would be reversed. The ledger account 50000 would have a budget amount of $10,000. 

You can view the budget register entries for the original budget by selecting the budget account entry on the **Budget account entries** FastTab on the **Budget resister entry** page. On the menu bar, click **Related information**, and then click **Budget register entries**.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
