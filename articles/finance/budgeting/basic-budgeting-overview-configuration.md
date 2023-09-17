---
# required metadata

title: Budgeting overview
description: Almost every company that uses Financials functionality in Microsoft Dynamics 365 Finance will have to be able to create reports of budget vs. actuals. This article explains the minimum configuration that is required in order to create budgets in finance and operations or load them from a third-party program.
author: panolte
ms.date: 04/29/2021
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 28a9793e-d376-47af-a345-69046bad17df
ms.search.region: global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Budgeting overview

[!include [banner](../includes/banner.md)]

Almost every company that uses Financials functionality in Microsoft Dynamics 365 Finance will have to be able to create reports of budget vs. actuals. This article explains the minimum configuration that is required in order to create budgets in finance and operations or load them from a third-party program.

## Overview

The approved budget for a legal entity is maintained in a document that is known as a *budget register entry*. The lines in a budget register entry document are known as *budget account* entries, and contain financial dimension information, dates, and the amounts of the approved budget. The budget register entry document is integrated with basic financial reports and inquiry pages where ledger actual amounts are compared to budget amounts. 

There are multiple methods for creating budget register entries:

-   Manually enter the document information on the **Budget register entries** page.
-   Use the Microsoft Excel template that you can open by clicking the **Open in Excel** button on the **Budget register entries** page.
-   Use the **Budget Account Entries** data entity in Data management to import budget register entries. You should consider using this method and turning on the **Set based processing** parameter when you must import many budget account entries into the system.
-   If the company uses Budget planning functionality to prepare budget data, you can use the **Generate budget register entry** periodic process.

The budget register entry is considered completed when the budget balances have been updated. On the **Budget register entries** page, click **Update budget balances** for a selected budget register entry or multiple entries. After you update the budget balances, the status of the budget register entry changes to **Completed**. Completed budget register entry can't be re-opened for edits. Therefore, if the budget data must be adjusted, you must create a new budget register entry instead of correcting data in the completed budget register entry.

## Configuration
When you configure budgeting, start on the **Budgeting parameters** page. On this page, you must define the budget journal, the number sequence for budget register entries, and the default behavior in the workspaces.

Next, if there are policies that govern the approval of budget register entries, based on budget type (for example, transfers or revisions), you must create budget register entry workflows on the **Budgeting workflows** page. If there are scenarios where transfers might be allowed without workflow approval, you can define budget transfer rules to support those scenarios. 

On the **Budgeting dimensions** page, you must select the financial dimensions that are used for budgeting, based on the dimensions that are used in the chart of accounts. You can select all financial dimensions or a subset of them for budgeting.

Define a *budget model* that corresponds to all or some of the budgets. You can use a single budget model for all budget register entries. Alternatively, you can create separate models that are based on the budget type, the geographical location, or some other way that a budget can be classified. 

> [!NOTE] 
> If budget control is used, you can associate only one budget model with a specific budget cycle time span. 

Create *budget codes* that identify the type of budget transactions to record and any related workflow. Budget codes can support the following budget types:

-   Original budget
-   Transfer
-   Revision
-   Encumbrance
-   Pre-encumbrance
-   Carry-forward budget

Budget codes let you have an audit trail of approved budget modifications throughout the course of the budget cycle. If a workflow is associated with a budget code, the workflow will be enabled for all budget register entries that use that budget code, and workflow steps must be completed before the budget register entry can reach the **Completed** stage.  

You can also optionally set up *budget transfer rules*. To use budget transfer rules, select **Use rules for budget transfers** on the **Budget parameters** page. When budget transfer rules are used, if a user creates a document by using a budget code of the **Transfer** type, budget balances won't be updated if the budget transfer rules are violated. For example, you can allow budget transfer documents where the expense budget is transferred between the main accounts for the Sales and Marketing department, but can prohibit budget from being transferred from or to that department unless workflow approval has been granted for that type of budget account entry.

Functionality that was introduced in Microsoft Dynamics 365 Finance version 10.0.7 (January 2020) added capability and flexibility for budget register entries. To enable these enhancements, go to the **Feature management** workspace and select **Budget register entries for quantity only** and/or **Budget register entries defaulting of amount type**.

The **Budget register entries for quantity** only feature lets you post a budget register entry with quantity-only amounts. For example, you could post a budget entry with a quantity of 32 and a price of zero, which results in an amount of zero. You can then use this quantity within the context of a financial report to determine a price per quantity. Note that no inquiries or reports were updated as part of this feature; the feature just enables you to post an amount of zero.

The **Budget register entries defaulting of amount type** feature allows the default amount type within a budget register entry to be an amount type other than expense. The budget register entry line now will default to expense when the main account type is expense; it will default to revenue when the main account type is revenue; and it will default to expense for all other account types.

## Using workspaces and inquiry pages to track budget vs. actuals
The budget manager can review the current state of a budget in the **Ledger budgets and forecasts** workspace. The **Expense over budget** and **Revenue under budget** tabs provide a quick view of the financial dimension combinations where budget targets aren't being met or are approaching the threshold. You can personalize the budget threshold percentage and financial dimension sets that are used on those tabs by clicking **Configure my workspace**. You can click **Unit managers** to see the workers who are responsible for specific financial dimension combinations that are selected on those tabs. For example, if you see that the expense budget of the Operations department is going over the budget threshold, you can easily find and contact the Operations department manager to discuss the issue. 

> [!NOTE] 
> The **Department manager** field on the **Organization Units** page determines which managers support specific financial dimension combinations. Click **See more** at the bottom of the tab to open the **Budget vs actuals** inquiry page for more details about budget amounts versus actual amounts. 

The **Actual vs budget** inquiry page lets you drill into the details of the budget versus actual amounts. Select a line on the inquiry page, and then click **Period balances** to see budget and actual amounts spread across fiscal periods. The **Budget account entries** page provides drill-through to the details of the budget amount in budget register entries. The **General journal entries** page opens the ledger transactions that are included in the calculated **Actuals** amount. 

A company that is using Budget planning functionality can create and use *budget forecasts* in the **Ledger budgets and forecasts** workspace.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]

