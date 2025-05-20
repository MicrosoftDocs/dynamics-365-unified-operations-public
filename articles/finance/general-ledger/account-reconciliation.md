---
title: Account reconciliation
description: Learn how to use the Account reconciliation page and the Copilot agent that integrates with it.
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 05/10/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-03-23
ms.search.form: ReconciliationAutomationWorkspaceOverviewPage, ReconciliationAutomationSnapshot, ReconciliationAutomationWorkspaceExceptionsTaskPage, ReconciliationAutomationWorkspaceReconciledTransactionsPage
ms.dyn365.ops.version: 10.0.42
---

# Account reconciliation

Starting in Microsoft Dynamics 365 Finance version 10.0.44, the Account reconciliation feature is available. The feature is used instead of the old reactive SSRS reports used for reconciling your general ledger with the subledgers of accounts payable, accounts receivable, tax and bank. It's a workspace to view reconciled data as well as automated data analysis on a defined schedule, allowing the processing to happen in the background and in off hours only if desired.  The exceptions shown on the workspace allow you to take action directly and when the Microsoft CoPilot powered agent is enabled it provides suggestions to the most likely action to take, saving time in the account reconciliation process each period end. 

## Account reconciliation workspace page

To access the **Account reconciliation workspace**, go to **Workspaces** > **Account reconciliation**. This page displays open exceptions for the current period, as well as any agent recommended actions, addressed exceptions, and any automatically reconciled transactions in the summary cards near the top of the page. Use the filter options at the top of the page to adjust the data you wish to view on the workspace, such as changing from the current fiscal period to the prior fiscal period.  

In the bottom section of the workspace page you find details per each module and each company in that module that has transactional data for the period selected. The **Status** column has a button that displays the number of exceptions to deal with or indicates **Fully reconciled** status when all exceptions are dealt with. 

[![Account Reconciliation workspace](./media/AccountReconciliationWorkspace.png)](./media/AccountReconciliationWorkspace.png)

## Copilot agent for account reconciliation

To setup and configure the copilot powered agent for the Account reconciliation agent, see [Set up and configure the Account Reconciliation Agent](acct-rec-agent.md)

## Dealing with exceptions

If there are exceptions to address, click **Mitigate exceptions** on the **Open exceptions** card to view all exceptions for all modules across all legal entities. To navigate to the mitigate exceptions page, click **Red status** for a given module and a specific legal entity. 

The **Open exceptions** page allows you to view the details of each exception and take proper action to reconcile each exception. 
When the exception is **In Subledger not in ledger** the following actions are available:
- **Create journal entry** - Users are taken to the General journal where an adjusting entry can be created to address the exception.
- **Link transactions** - Usera taken to the **Link transactions** page where they can link transactions that are **In subledger not ledger** and **In ledger not subledger**.
- **Accept without change** - Exception are cleared and accepted as is. Commonly used when the difference is a small amount or rounding difference.
- **View exception history** - Users can view the history of the exception.

When the exception is **In Ledger not in subledger**, the following actions are available:
- **Reverse general ledger voucher** - Create a reversing entry for the ledger voucher.
- **Link transactions** - Go to the **Link transactions** page where transactions can be linked. 
- **Accept without change** - Exceptions are cleared and accepted as is. Commonly used when the difference is a small amount or rounding difference.
- **Create adjusting journal entry** - Go to the **General journal** where an adjusting entry can be created to address the exception.

When the exception is **Amount mismatch** the following actions are available:
- **Accept without change** - Exceptions are cleared and accepted as is. Commonly used when the difference is a small amount or rounding difference.
- **Create adjusting journal entry** - Users are taken to the **General journal** where an adjusting entry can be created to address the exception.

 ### Undo an action
 If you have marked an exception as addressed and want to change the way the exception was addressed, you may chose to undo the last action. When you **Undo** an addressed exception, the exception is moved back to the list of the open exceptions for you to take action once again. Click **Undo** prompts you for a reason to be entered, and click **OK** to proceed. 

## Snapshots

The last column of the main grid in the lower portion of the workspace page is a snapshot of data for the selected period, module, and company combination. The snapshot provides a final summary of all data for the given period including the automatically reconciled transactions and any addressed exceptions you might have dealt with for the period. The snapshot is only available for a ledger calendar fiscal period that is marked as on-hold or permanently closed and is fully reconciled. The generation of the snapshot happens with the same background process and schedule. 

## Configuration

Using the gear icon on the top right of the workspace page to view the settings and configuration for the account reconciliation feature. On the **Account reconciliation configuration** page you can enable or disable the reconciliation processing for each module. You can view and add/remove accounts used for each module for each legal entity. The list of accounts listed are prepopulated from the existing posting profile setup, bank and tax account setup in each legal entity. 

## Frequently asked questions

The workspace doesn't show any data, what can I do?
- Verify the last time and next runtime at the top right portion of the workspace. There's an indication similar to: "Data last updated 30 minutes ago, next update in 1 hour".
- For testing purposes - you can adjust the frequency and next runtime in the process automation - background processes for the **Automatic account reconciliation process** process. For production use, consider the impact of when and how frequently you want the process to execute and set the appropriate schedule.  
- Check the system batch job is waiting and not withhold status in the batch jobs page. Look for the **Process automation polling system** job.

I have chosen the action to create a journal, but I didn't actually create or post the journal and the voucher has been moved to the addressed exception page, what can I do? 
View the addressed exceptions and click **Undo** to move the exception back to the open exceptions list to be reprocessed accordingly. 
 
 
