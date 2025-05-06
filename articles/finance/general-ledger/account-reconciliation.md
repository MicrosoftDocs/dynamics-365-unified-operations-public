---
title: Account reconciliation
description: Learn how to use the account reconciliation page and the Copilot agent that integrates with it.
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 04/30/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-03-23
ms.search.form: ReconciliationAutomationWorkspaceOverviewPage, ReconciliationAutomationSnapshot, ReconciliationAutomationWorkspaceExceptionsTaskPage, ReconciliationAutomationWorkspaceReconciledTransactionsPage
ms.dyn365.ops.version: 10.0.42
---

# Account reconciliation

This feature is available as of Microsoft Dynamics 365 Finance version 10.0.44. The feature can be used instead of the old reactive SSRS reports used for reconciling your general ledger with the subledgers of Accounts Payable, Accounts Receivable, Tax and Bank. The feature provides a workspace for viewing the reconciled data as well as automation that does the data analysis on a schedule you can define, allowing the processing to happen in the background and in off hours only if desired.  The exceptions shown on the workspace allow you to take action directly and when the Microsoft CoPilot powered agent is enabled it will provide suggestions to the most likely action to take, saving you time in the account reconciliation process each period end. 

## Account reconciliation workspace page

To access the Account reconciliation workspace navigate to Workspaces – Account reconciliation. 

## Dealing with exceptions

If there are exceptions to address, click the mitigate exceptions button, to view all exceptions for all modules across all legal entities.  You can also navigate to the mitigate exceptions page by clicking on the red status button for a given module and a specific legal entity. 


## Frequently asked questions

Q) The workspace does not show any data, what can I do?
      1. Verify the last time and next runtime at the top right portion of the workspace.  There will be an indication similar to: "Data last updated 30 minutes ago, next update in 1 hour".
      2. For testing purposes - you can adjust the frequency and next runtime in the process automation - background processes for the process named 'Automatic account reconciliation process'
      3. Check the system batch job is waiting and not withold status in the batch jobs page. Look for the job named 'Process automation polling system job'.

Q) Question2
 
 
