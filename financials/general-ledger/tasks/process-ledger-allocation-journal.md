--- 
# required metadata 
 
title: Process ledger allocation journal
description: Use the Process allocation request page to create an allocation journal that can be reviewed and approved before posting to General ledger, or posted directly to General ledger. 
author: aprilolson
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Process ledger allocation journal

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use the Process allocation request page to create an allocation journal that can be reviewed and approved before posting to General ledger, or posted directly to General ledger. Before you can create an allocations journal, there must be least one active Ledger allocation rule. This task uses the USMF demo company.

1. Go to General ledger > Allocations > Process allocation request.
2. In the Rule field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the As of date field, enter a date.
    * The As of Date is very important when the Ledger is the Data source for the rule. This date controls which ledger balances to include for allocation.     In the Zero source field select Stop. This will  Stop the allocation process and display a message that states that a zero source amount is selected.  
6. In the Proposal options field, select 'Proposal only'.
    * Select Proposal only to review and optionally approve the result in Allocation journals prior to posting the allocation to General ledger.  
7. In the GL posting date field, enter a date.
8. Click OK.
9. Go to General ledger > Allocations > Allocation journals.
10. Click Lines.
11. Click Post.
12. Click Post.

