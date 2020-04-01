--- 
# required metadata 
 
title: Configure wave processing
description: This guide describes how to set up the criteria that determine what work is generated for a warehouse when a wave is processed, and whether waves are processed manually or automatically. 
author: ShylaThompson
manager: AnnBe 
ms.date: 07/01/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWaveTemplateTable, InventLocationIdLookup, WHSParameters, ProdParameters   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Configure wave processing

[!include [banner](../../includes/banner.md)]

This guide describes how to set up the criteria that determine what work is generated for a warehouse when a wave is processed, and whether waves are processed manually or automatically. You specify the criteria by setting up wave templates and queries that match a wave with released lines in sales orders, production orders, or kanban orders. Wave processing is used in warehouses that use the functionality in the Warehouse management module, and not those that use the functionality in the Inventory management module. You can run this procedure in demo data company USMF.

1. Go to **Navigation pane > Modules > Warehouse management > Setup > Waves > Wave templates**.
2. Click **New**.
3. In the **Wave template name** field, type a value. When you set up a wave template, you specify the sequence in which the templates will be matched to released lines on sales orders, production orders, or kanbans. When a line is released to the warehouse or to production, it uses the first wave template that it meets the criteria for. We recommend that you put templates with the most specific criteria at the top of the list. The broader the criteria, the more likely it is for a line to meet the criteria, and this could lead to lines being assigned to the wrong wave.  
4. In the **Wave template description** field, type a value.
5. In the **Site** field, enter or select a value. If you're using USMF, you can select site 2.  
6. In the **Warehouse** field, enter or select a value. If you're using USMF, you can select warehouse 24.  
7. Set the **Automate wave creation** field to **Yes**. Select this option to automatically create a wave when a sales order, production order, or kanban is released to the warehouse.  
8. Set the **Process wave at release to warehouse** option to **Yes**. Select this option to automatically process the wave and create work when a line is released to the warehouse.  
9. Set the **Automate wave release option** to **Yes**. Select this option to automatically release the wave. The picking work is created and made available on mobile devices.  
10. Set the **Assign to open waves option** to **Yes**. Lines are assigned to waves based on the query filter for the wave template.  
11. Set the **Process wave automatically at threshold option** to **Yes**. Select this option to automatically process the wave when its values reach the thresholds for weight, shipment, and lines specified in the Wave thresholds field group. This option is available only if Shipping is selected in the Wave template type field.  
12. Set the **Automate replenishment work release option** to **Yes**. Select this option to create demand-based replenishment work and release it automatically. You must add the replenishment wave method to the wave template, and create a replenishment template of the type Wave demand.  
13. Expand the **Methods** section.

    - Wave template methods allow you to control the sequence of activities that each wave is going through when it's processed. For example, you might have a method for wave replenishment. When you add a method, it's automatically listed in the appropriate location in the sequence of steps. If you've set the Automate replenishment work release option to Yes, you need to add the replenish method here.  
    - Wave attributes act as filters, to restrict the kind of items that can use the wave. For example, you could specify an item group.  
14. Click **Save**.
15. Close the page.
16. Go to **Warehouse management > Setup > Warehouse management parameters**.
17. Expand the **Wave processing** section.
18. In the **Wave processing batch group** field, enter or select a value.
19. Set the **Process waves in batch option** to **Yes**.
20. In the **Wait for lock (ms)** field, enter a number. Enter the time, in milliseconds, that an allocation step will wait for a system resource that is locked by another allocation step. When this time is exceeded, the wave is not processed and an error message is displayed.  
21. Click **Save**.
22. Close the page.
23. Go to **Navigation pane > Modules > Production control > Setup > Production control parameters**.
24. In the **Release to warehouse** field, select an option.

For sales orders and kanban orders, inventory must be reserved before the order is released to the warehouse. Otherwise, the items or allocation lines cannot be processed in a wave. For production orders, you also have the option of choosing Allow partial reservation. For example, this is useful if you have the materials that you need to start production, and can then wait until the additional materials become available to finish the process. If you select this option, you must manually repeat the release to warehouse process when the additional materials become available.  
25. Close the page.

