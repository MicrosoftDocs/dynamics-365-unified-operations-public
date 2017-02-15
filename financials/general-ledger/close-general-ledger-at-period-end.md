---
# required metadata

title: Close the general ledger at period end
description: This topic describes the tasks that are typically completed when performing a period closing for General ledger. 
author: RobinARH
manager: AnnBe
ms.date: 2015-12-02 23 - 07 - 25
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2231
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 14111
ms.assetid: 911ff75e-48e0-4f0f-966b-ad48a904efa6
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Close the general ledger at period end

This topic describes the tasks that are typically completed when performing a period closing for General ledger. 

In General ledger, you can complete closing procedures for a period or a year. Closing processes prepare the system for a new period. To prepare the system for a new year, you must run the year end close process. Each organization has different processes and steps that it performs for the end of a period. Here are some optional steps for period ends:

-   Complete all the tasks for all other modules, such as Accounts receivable, Accounts payable, and Inventory.
-   Verify that all journals are posted.
-   Run foreign currency revaluation to generate any unrealized gain or loss amounts.
-   Settle transactions for each ledger account.
-   Process any required allocations.
-   Manually post period-end adjustments.
-   Journalize transactions, and review the **Ledger journal** report.
-   Perform a consolidation by using a consolidation company or Financial reporting.
-   Generate period-end financial statements by using Financial reporting.
-   Set ledger periods to **On hold**, so that no further posting occurs. You can also restrict a period to a specific user group while period-end activities are occurring, for better control. It's not a good idea to set periods to **Permanently closed**, because you can't reopen a period that has been closed.

The Financial period close workspace can be used to organize and track the tasks required for various period end processes. Refer to the [Financial period close workspace](financial-period-close-workspace.md)topic for additional information.

See also
--------

[Year end close](https://ax.help.dynamics.com/en/?post_type=incsub_wiki&p=246674)

