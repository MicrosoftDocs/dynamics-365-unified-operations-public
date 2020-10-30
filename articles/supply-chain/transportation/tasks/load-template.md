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

## Load Templates

When you create a new load, you can assign a load template that contains information about equipment and measures such as height, width, depth, and volume of the load.

This topic describes how to set up load templates and how to associate a load template with a new load.

To set up load templates, follow these steps:

1. Go to **Transportation management \> Setup \> Load Building \> Load template**.
1. On the Action Pane, select **New** to add a new template or **Edit** to edit an existing one.
1. Make the following settings for your new or existing template row:
    - **Load template ID** - Enter a unique identifier (ID) for the load template.
    - Equipment field, select the equipment to use for shipping the load.
1. In the **Load height**, **Load width**, and **Load depth** fields, enter the dimensions of the load.
1. In the **Max. allowed load volume** and **Max. allowed load weight** fields, enter the maximum allowed volume and weight of the load.
1. In the *Maximum allowed gross weight* field, enter the maximum allowed gross weight of the load. The load's gross weight includes both its tare weight and its loading weight.
1. In the **Maximum number of freight pieces allowed** field, enter the maximum number of freight pieces that the load can contain.
1. Select the **Stack load on floor** check box if you want to use floor loading. In a floor loading scenario, boxes are stacked floor-to-ceiling, wall-to-wall inside the container to maximize capacity.

## Associate a load template with a new load

To associate a load template with a new load, follow these steps:

1. Go to **Transportation management \> Planning \> Load planning workbench**.
1. Select **To new load**.
1. In the **Load template ID** field, select a template.
