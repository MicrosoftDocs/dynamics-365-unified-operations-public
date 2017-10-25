--- 
# required metadata 
 
title: Propose and post accelerated depreciation (Japan)
description: For Japan, you can propose an accelerated depreciation based on the data on confirmed accelerated depreciation documents. 
author: ShylaThompson
manager: AnnBe 
ms.date: 02/26/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Propose and post accelerated depreciation (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, you can propose an accelerated depreciation based on the data on confirmed accelerated depreciation documents. Note: The accelerated depreciation proposal will not propose ordinary depreciation. This procedure must be completed after you post ordinary depreciation.



This procedure walks you through proposing and posting an accelerated depreciation document based on confirmed accelerated depreciation documents. 



In order to complete this procedure, the Fixed asset configuration key must be selected.



This procedure was created using the demo data company JPMF.

1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Accelerated depreciation proposal.
8. In the To date field, enter a date.
    * By default, the criteria is configured to propose all confirmed accelerated depreciation documents. You can change this if there is any other needs such as proposing for one specific document.  
9. Click OK.
    * Confirm that the accelerated depreciation was proposed.  
    * Note: The ordinary depreciation is not handled, and therefore, still needs user's operation to propose and post it.  
10. Click Post.
11. Close the page.
12. Go to Fixed assets > Periodic tasks > Accelerated depreciation > Accelerated depreciation document.
    * Confirm that the status of posted document has been updated.  

