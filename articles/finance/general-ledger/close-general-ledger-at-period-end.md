---
# required metadata

title: Close the general ledger at period end
description: This article describes the tasks that are typically completed when performing a period closing for General ledger. 
author: aprilolson
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerPeriodCloseWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: cec9e039-c1a2-482c-bea6-e11d896eea9d
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Close the general ledger at period end

[!include [banner](../includes/banner.md)]

This article describes the tasks that are typically completed when performing a period closing for General ledger. 

In General ledger, you can complete closing procedures for a period or a year. Closing processes prepare the system for a new period. To prepare for a new year, you must run the year end close process. Each organization has different processes and steps that it performs for the end of a period. Here are some optional steps for period ends:

-   Complete all the tasks for all other modules, such as Accounts receivable, Accounts payable, and Inventory.
-   Verify that all journals are posted.
-   Run foreign currency revaluation to generate any unrealized gain or loss amounts.
-   Settle transactions for each ledger account.
-   Process any required allocations.
-   Manually post period-end adjustments.
-   Journalize transactions, and review the **Ledger journal** report.
-   Perform a consolidation by using a consolidation company or Financial reporting.
-   Generate period-end financial statements by using Financial reporting.
-   Set ledger periods to **On hold**, so that no further posting occurs. You can also restrict a period to a specific user group while period-end activities are occurring, for better control. It's not a good idea to set periods to **Permanently closed**, because you can't reopen a period that has been closed.

The **Financial period close** workspace can be used to organize and track the tasks required for various period end processes. 


For more information, see the following topics for more information:
- [Financial period close workspace](financial-period-close-workspace.md) 
- [Year-end close](Year-end-close.md)  
- [Mass financial period close](tasks/mass-financial-period-close.md)






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
