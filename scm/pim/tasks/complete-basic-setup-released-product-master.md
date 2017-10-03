--- 
# required metadata 
 
title: Complete basic setup of a released product master
description: This procedure shows how to complete the minimum setup that is required before the product master can be used in BOM versions. 
author: YuyuScheller
manager: AnnBe 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: yuyus
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Complete basic setup of a released product master

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to complete the minimum setup that is required before the product master can be used in BOM versions.

This is the third procedure out of eight which explains how to build combinations for dimension-based configuration. The demo data company used to create this procedure is USMF.

1. Go to Product information management > Products > Released products.
2. In the list, find and select the desired record.
    * Select the product master that you have released in the second procedure. This product master is created with the dimension-based configuration technology.  
3. On the Action Pane, click Product.
4. Click Dimension groups to open the drop dialog.
5. In the Storage dimension group field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
    * The storage dimension group determines which storage dimensions are used for product transaction. Select Site for this procedure.  
7. In the list, click the link in the selected row.
8. In the Tracking dimension group field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
    * The tracking dimension group determines which tracking dimensions are used for product transaction. Select None for this procedure.  
10. In the list, click the link in the selected row.
11. Click OK.
12. In the list, click the link in the selected row.
13. Click Edit.
    * Open the Released product details form to continue the setup task.  
14. In the Item model group field, click the drop-down button to open the lookup.
15. In the list, find and select the desired record.
    * Item model groups contain settings that determine how items are controlled and handled on item receipts and issues. They also determine how item consumption is calculated. Select   FIFO for this procedure.  
16. In the list, click the link in the selected row.
17. Expand or collapse the Manage costs section.
18. In the Item group field, click the drop-down button to open the lookup.
19. In the list, find and select the desired record.
    * Item groups are used to manage inventory by dividing inventory items into groups. Select   CarAudio for this procedure.  
20. In the list, click the link in the selected row.
21. On the Action Pane, click Plan.
22. Click Default order settings.
23. In the Default order type field, select an option.
    * Select Production to specify that the default supply option for this product master is to produce it.  
24. Close the page.
25. Close the Released product details form.

