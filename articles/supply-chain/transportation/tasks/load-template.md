--- 
# required metadata 
 
title: Load templates
description: This topic describes how to set up load templates and how to associate a load template with a new load. 
author: Henrikan
manager: 
ms.date: 10/30/2020
ms.topic: business-process 
ms.prod: 
ms.service: dynamics-ax-applications 
ms.technology: 
 
# optional metadata 
 
ms.search.form: WHSLoadTemplate 
audience: Application User 
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Distribution
ms.author: henrikan
ms.search.validFrom: 2020-10-30 
ms.dyn365.ops.version: 10.0.15
---

# Load Templates

When you create a new load, you can assign a load template that contains information about equipment and measures such as height, width, depth, and volume of the load.

This topic describes how to set up load templates and how to associate a load template with a new load.

To set up load templates, follow these steps:

1. Go to **Transportation management \> Setup \> Load Building \> Load template**.
1. On the Action Pane, select **New** to add a new template or **Edit** to edit an existing one.
1. Make the following settings for your new or existing template row:
    - **Load template ID** - Enter a unique identifier (ID) for the load template.
    - **Equipment** - Select the equipment to use for shipping the load.
    - **Load height**, **Load width**, and **Load depth** - Enter the dimensions of the load.
    - **Max. allowed load volume** and **Max. allowed load weight** - Enter the maximum allowed volume and weight of the load.
    - **Maximum allowed gross weight** - Enter the maximum allowed gross weight of the load. The load's gross weight includes both its tare weight and its loading weight.
    - **Maximum number of freight pieces allowed** - Enter the maximum number of freight pieces that the load can contain.
    - **Stack load on floor** - Select this check box if you want to use floor loading. In a floor loading scenario, boxes are stacked floor-to-ceiling, wall-to-wall inside the container to maximize capacity.
1. On the Action Pane, select **Save**.

## Associate a load template with a new load

To associate a load template with a new load, follow these steps:

1. Go to **Transportation management \> Planning \> Load planning workbench**.
1. On the Action Pane, open the **Supply and demand** tab and, from the **Add** group, select **To new load**. <!-- KFM: What are we assigning to? Do we need to select a shipment or load or something here? -->
1. The **Load template** dialog box opens. In the **Load template ID** field, select the template you want to apply.
1. Select **OK** to apply the template.

<!-- KFM: The load building workbench appears also to use load templates. Shouldn't we mention that? We could link to the existing topic. -->