---
title: Load templates
description: Learn how to set up load templates, and how to associate a load template with a new load, including a step-by-step process.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: WHSLoadTemplate, WHSOutboundLoadPlanningWorkbench, WHSInboundLoadPlanningWorkbench
ms.topic: how-to
ms.date: 07/30/2024
ms.custom: 
  - bap-template
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

1. Go to one of the following pages, depending on whether you're setting up an inbound or outbound load:
    - **Transportation management > Planning > Inbound load planning workbench**.
    - **Transportation management > Planning > Outbound load planning workbench**.

1. In the upper part of the page, select one of the following tabs, depending on the type of source document that you're creating a load for: **Shipments**, **Sales lines**, **Transfer lines**, or **Purchase order lines**.
1. Select the specific document to plan the load for.
1. On the Action Pane, on the **Supply and demand** tab, in the **Add** group, select **To new load**.
1. In the **Load template** dialog box, in the **Load template ID** field, select the template to apply.
1. Select **OK** to apply the template.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
