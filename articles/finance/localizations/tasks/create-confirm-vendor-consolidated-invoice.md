--- 
# required metadata 
 
title: Create and confirm a vendor consolidated invoice
description: In Japan, sales and purchase invoices during the month are consolidated at the end of the month to calculate the due amount. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendConsInvoice_JP   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and confirm a vendor consolidated invoice

[!include [banner](../../includes/banner.md)]

In Japan, sales and purchase invoices during the month are consolidated at the end of the month to calculate the due amount. 



This task walks you through creating and confirming a vendor consolidated invoice.



Before you can complete this task, you must have posted purchase invoices. 



This task was created using the demo data company JPMF.

1. Go to Accounts payable > Periodic tasks > Consolidated invoice.
2. Click New.
3. In the Execution date field, enter a date.
4. Select or clear the Use consolidation date specified below check box.
    * If you want to override the consolidation date, you must set the Use consolidation date slider to be 'Yes'.  
5. In the Consolidation date field, enter a date.
    * Example: When the consolidation date is the 25th, you can run the consolidation on the 24th if you set this slider to 'Yes'. You will have to manually specify a Consolidation date.  
6. Click OK.
    * Verify the generated  consolidate invoice.  
7. In the list, click the link in the selected row.
    * Switch to the detail view of the Consolidated invoice page by clicking on the Consolidation ID of the Consolidated invoice in the grid.  
    * Verify that the invoiced purchase orders are included in the consolidated invoice.  
8. Click Confirm.

