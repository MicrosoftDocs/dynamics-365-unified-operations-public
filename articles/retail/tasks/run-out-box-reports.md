--- 
# required metadata 
 
title: Generate and run out-of-box reports
description: Use this task guide to run out of box reports in headquarters from different workspaces and Inquiries & Sales reports located under Retail & Commerce. 
author: ashishmsft
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
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Generate and run out-of-box reports

[!include[task guide banner](../includes/task-guide-banner.md)]

Use this task guide to run out of box reports in headquarters from different workspaces and Inquiries & Sales reports located under Retail & Commerce.



The demo data company used to create this recording is USRT. This recording is intended for the System administrator role.


## Launch reports from workspaces
1. Go to Retail and commerce > Products and categories > Category and product management.
2. Click the arrow to expand or collapse the Reports section.
3. Click Top products report.
4. In the From date field, enter a date.
5. In the To date field, enter a date.
6. In the Channel field, click the drop-down button to open the lookup.
7. In the tree, select 'Contoso Retail\Contoso Retail USA\Central\Houston'.
    * This shows the default retail organization hierarchy for Retail reporting purpose.   Go to Organization administration >Organizations >Organization hierarchy purposes and choose Retail reporting and under Assigned hierarchies, check the hierarchy name for which Default column is checked.      As part of demo data (used for this task recording) you would notice, Retail Stores by Region, is the default organization hierarchy for the Retail reporting purpose.     
8. Click OK.
9. In the View field, select an option.
10. In the By field, select an option.
11. Click OK.

## Launch reports from the inquiries and sales reports located under Retail & Commerce app link.
1. Go to Retail and commerce > Inquiries and reports > Sales reports > Category sales report.
2. In the From date field, enter a date.
3. In the To date field, enter a date.
4. In the Channel field, click the drop-down button to open the lookup.
5. In the tree, select 'Contoso Retail\Contoso Retail USA\West\Seattle'.
    * This shows the default retail organization hierarchy for Retail reporting purpose.   Go to Organization administration >Organizations >Organization hierarchy purposes and choose Retail reporting and under Assigned hierarchies, check the hierarchy name for which Default column is checked.      As part of demo data (used for this task recording) you would notice, Retail Stores by Region, is the default organization hierarchy for the Retail reporting purpose.     
6. Click OK.
7. Click OK.

## Export an HQ reports
1. Go to Retail and commerce > Inquiries and reports > Sales reports > Organization sales report.
2. In the From date field, enter a date.
3. In the To date field, enter a date.
4. Click OK.
5. Click Export.
6. Click PDF.

