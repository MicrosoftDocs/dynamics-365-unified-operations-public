--- 
# required metadata 
 
title: Complete basic setup of a released product master
description: This topic shows how to complete the minimum setup that is required before the product master can be used in BOM versions.  
author: t-benebo
ms.date: 07/08/2019
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductDetailsExtended, InventTableInventoryDimensionGroups, InventItemOrderSetup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Complete basic setup of a released product master

[!include [banner](../../includes/banner.md)]

This topic shows how to complete the minimum setup that is required before the product master can be used in BOM versions.

This is the third procedure out of eight which explains how to build combinations for dimension-based configuration. The demo data company used to create this procedure is USMF.

1. Go to **Navigation pane > Modules > Product information management > Products > Released products**.
2. In the list, find and select the desired record. Select the product master that you have released in the second procedure. This product master is created with the dimension-based configuration technology.  
3. On the Action Pane, select **Product**.
4. Select **Dimension groups** to open the drop dialog.
5. In the **Storage dimension group** field, select the drop-down button to open the lookup.
6. In the list, find and select the desired record. The storage dimension group determines which storage dimensions are used for product transaction. Select **Site** for this procedure.  
7. In the **Tracking dimension group** field, select the drop-down button to open the lookup.
8. In the list, find and select the desired record. The tracking dimension group determines which tracking dimensions are used for product transaction. Select **None** for this procedure.  
9. Click **OK**.
10. Click **Edit**.
11. In the **Item model group** field, select the drop-down button to open the lookup.
12. In the list, find and select the desired record. Item model groups contain settings that determine how items are controlled and handled on item receipts and issues. They also determine how item consumption is calculated. Select **FIFO** for this procedure.  
13. Expand the **Manage costs** section.
14. In the **Item group** field, select the drop-down button to open the lookup.
15. In the list, find and select the desired record. Item groups are used to manage inventory by dividing inventory items into groups. Select **CarAudio** for this procedure.  
16. On the Action Pane, select **Plan**.
17. Select **Default order settings**.
18. In the **Default order type field**, select an option. Select **Production** to specify that the default supply option for this product master is to produce it.  
19. Select **Save**.
20. Close the page.
21. Close the **Released product details** form.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]