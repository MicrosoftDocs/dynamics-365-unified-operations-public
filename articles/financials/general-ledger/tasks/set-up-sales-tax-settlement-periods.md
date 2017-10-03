--- 
# required metadata 
 
title: Set up sales tax settlement periods
description: Sales tax settlement periods contain information about the period intervals for which sales tax needs to be reported and paid. 
author: twheeloc
manager: AnnBe 
ms.date: 11/14/2016
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
ms.author: vstehman
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up sales tax settlement periods

[!include[task guide banner](../../includes/task-guide-banner.md)]

Sales tax settlement periods contain information about the period intervals for which sales tax needs to be reported and paid. A settlement process can be run for a settlement period for a specific date interval. All tax codes associated with the settlement period will be settled. Depending on the set up of the related Sales tax authority, the tax liability is posted either to a vendor or a General ledger account.



This task uses the USMF demo company.



1. Go to Tax > Indirect taxes > Sales tax > Sales tax settlement periods.
2. Click New.
3. In the Settlement period field, type a value.
4. In the Description field, type a value.
5. In the Authority field, select the sales tax authority that receives the reports and the payments that are created for the settlement period.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the Terms of payment field, click the drop-down button to open the lookup.
    * The related Sales tax authority can be set up as a vendor and the Sales tax settlement will create an open vendor invoice. The Terms of payment defines the Due date for the open vendor invoice.  
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
11. Select a type for the settlement period intervals.
12. Enter the number of Period interval units per period. For example, a quarter has 3 months.
13. Select or clear the Use batch processing for sales tax settlement check box.
    * The settlement process for the settlement period can be processed as batch job in the background. This is recommended for a large number of tax transactions within a period interval.  
14. Expand the Period intervals tab.
15. Click Add.
16. In the list, mark the selected row.
17. In the From date field, enter a date.
18. In the To date field, enter a date.
19. Click New period interval.
    * Once the first period interval has been entered, new periods can be created automatically. You can come back and add new period intervals as required.  
20. Close the page.

