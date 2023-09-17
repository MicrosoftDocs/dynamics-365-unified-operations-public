--- 
# required metadata 
 
title: Load templates
description: This article describes how to set up load templates, and how to associate a load template with a new load.
author: Weijiesa
ms.date: 10/30/2020
ms.topic: how-to 
ms.prod: 
ms.technology: 
 
# optional metadata 
 
ms.search.form: WHSLoadTemplate 
audience: Application User 
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2020-10-30 
ms.dyn365.ops.version: 10.0.15
---

# Load templates

[!include [banner](../../includes/banner.md)]

When you create a new load, you can assign a load template. The load template contains information about equipment, and about measures such as the height, width, depth, and volume of the load.

This article describes how to set up load templates, and how to associate a load template with a new load.

## Set up a load template

1. Go to **Transportation management \> Setup \> Load Building \> Load template**.
1. On the Action Pane, select **New** to add a new template or **Edit** to edit an existing template.
1. In the row for the new or existing template, set the following fields:

    - **Load template ID** – Enter a unique identifier (ID) for the load template.
    - **Equipment** – Select the equipment that should be used to ship the load.
    - **Load height**, **Load width**, and **Load depth** – Enter the dimensions of the load.
    - **Max. allowed load volume** and **Max. allowed load weight** – Enter the maximum allowed volume and weight of the load.
    - **Maximum allowed gross weight** – Enter the maximum allowed gross weight of the load. A load's gross weight includes both its tare weight and its loading weight.
    - **Maximum number of freight pieces allowed** – Enter the maximum number of freight pieces that the load can contain.
    - **Stack load on floor** – Select this check box to use floor loading. In a floor loading scenario, boxes are stacked floor to ceiling and wall to wall inside the container, to maximize capacity.

1. On the Action Pane, select **Save**.

## Associate a load template with a new load

1. Go to **Transportation management \> Planning \> Load planning workbench**.
1. In the upper part of the page, select one of the following tabs, depending on the type of source document that you're creating a load for: **Shipments**, **Sales lines**, **Transfer lines**, or **Purchase order lines**. 
1. Select the specific document to plan the load for.
1. On the Action Pane, on the **Supply and demand** tab, in the **Add** group, select **To new load**.
1. In the **Load template** dialog box, in the **Load template ID** field, select the template to apply.
1. Select **OK** to apply the template.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]