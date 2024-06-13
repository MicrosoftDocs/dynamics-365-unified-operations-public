--- 
title: Process ledger allocation journal
description: Learn how to process an allocation request in Dynamics 365 Finance, including a step-by-step process using the USMF demo company.
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 03/15/2023
ms.custom:
ms.reviewer: twheeloc     
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerAllocationRequest, LedgerJournalTable, LedgerJournalTransAllocation
ms.dyn365.ops.version: Version 7.0.0 
---

# Process ledger allocation journal

[!include [banner](../../includes/banner.md)]

This article explains how to process an allocation request. Use the **Process allocation request** page to create an allocation journal that can be reviewed and approved before posting to General ledger, or posted directly to General ledger. Before you can create an allocations journal, there must be least one active Ledger allocation rule. This task uses the USMF demo company.

1. Go to **General ledger > Allocations > Process allocation request**.
2. In the **Rule** field, select the desired record in the drop-down menu.
3. In the **As of date** field, enter a date.

    - The **As of Date** is very important when the **Ledger** is the Data source for the rule. This date controls which ledger balances to include for allocation.  
    - In the **Zero source** field select **Stop**. This will stop the allocation process and display a message that states that a zero source amount is selected.  

4. In the **Proposal options** field, select **Proposal only**. Select **Proposal only** to review and optionally approve the result in **Allocation journals** prior to posting the allocation to General ledger.  
5. In the **GL posting date** field, enter a date.
6. Select **OK**.
7. Go to **General ledger > Allocations > Allocation journals**.
8. Select **Lines**.
9. Select **Post**.
10. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
