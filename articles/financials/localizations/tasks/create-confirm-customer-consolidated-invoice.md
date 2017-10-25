--- 
# required metadata 
 
title: Create and confirm a customer consolidated invoice (Japan)
description: In Japan, sales and purchase invoices during the month are consolidated at the end of the month to calculate the due amount. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/16/2016
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
# Create and confirm a customer consolidated invoice (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, sales and purchase invoices during the month are consolidated at the end of the month to calculate the due amount. 



Use this task to learn how to create and confirm a consolidated invoice. 



In order to complete this task, the sales or purchase invoices should have been posted before running this task.



This task uses the JPMF demo company data.

1. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
2. Click New.
    * The default Execution date is the session date.  
    * Specify the Use consolidation date specified below slider to be 'Yes' if you want to override the consolidation date.  
    * Example: When the consolidation date is specified as the 25th, you can run the consolidation on the 24th if you set this slider to 'Yes'. You will have to manually specify a Consolidation date.  
3. Click OK.
    * Verify that the Consolidated invoice was generated.  
    * One Consolidated invoice will contain only one Customer account. When there are multiple Customer accounts to be consolidated, multiple consolidated invoices will be generated.  
4. In the list, click the link in the selected row.
    * Switch to the detail view of the Consolidated invoice page  by clicking on the Consolidation ID of the Consolidated invoice in the grid.  
    * Verify that invoiced sales orders are included in the consolidated invoice.  
5. Click Confirm.
    * The Status of the consolidated invoice changes to be 'Confirmed' after you click Confirm. When confirmed, the consolidated invoice will be locked and you cannot edit it.  

