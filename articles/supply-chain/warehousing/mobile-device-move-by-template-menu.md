---
title: Set up a mobile device menu item for moving items by template
description: Learn how to set up a mobile device menu item that lets workers register movements of items, including a step-by-step process.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 02/05/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItem
---

# Set up a mobile device menu item for moving items by template

[!include [banner](../includes/banner.md)]

This article explains how to set up a mobile device menu item that lets workers register movements of items in the warehouse. The worker doesn't decide where to move the items, but instead relies on the system to determine the target location based on the work template and/or location directive configured for the menu item.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. On the header of the new record, set the following fields:

    - **Menu item name** – Enter a unique name to identify the menu item.
    - **Title** – The title that you enter will be shown in the user interface (UI). It doesn't have to be unique.
    - **Mode** – Select *Work*. This value is required because this mobile flow involves work.
    - **Use existing work** – Set this option to *No*, because the work is created as the movement is done.

1. On the **General** FastTab, set the following fields:

    - **Work creation process** – Select *Movement by template*, because this type of work is what the menu item supports. The page is updated to provide settings that are relevant to this type of work.
    - **Display inventory status** – Set this option to *Yes* to show the inventory status on the device. Set it to *No* to use the default inventory status. If the items that are moved have only one inventory status, that status is the default status. If you use only one inventory status, you typically won't have to show this information.
    - **Use default data** – Set this option to *Yes* if you want specific data fields to be shown by default to workers who use the mobile app. Default data field values can provide information that workers typically need in their daily work. After you set this option to *Yes*, select **Default data** on the Action Pane to open a page where you can select the fields to show. For example, the *From location* field is often useful. Set this option to *No* if you don't want to select any default data for the menu item.
    - **Use process guide** – Set this option to *No*, because process guide isn't currently supported for movements of items.
    - **Barcode data policy** – Select the policy to use when multiple fields are filled in based on a single bar code scan. Learn more in [GS1 bar codes](gs1-barcodes.md).
    - **Generate license plate** – Set this option to *Yes* to automatically create new license plates as they're needed. Set it to *No* if the worker must always select an existing license plate. A license plate is needed if part of the quantity is moved from a license plate. A license plate is also needed if the "from" location isn't license plate controlled, but the "to" location is.
    - **Create movement** – Set to *Yes* to all workers to create work for a movement without requiring that the worker do the work immediately. This option is useful, for example, after a quality inspection has been completed and the inspector wants the item to be moved from the quality inspection area.
    - **Work template** – Select a work template to use when creating the movement work.
    - **Directive code** – To use a specific location directive, select the directive code that is associated the location directive.
    - **Override license plate during put** – Set to *Yes* to allow workers to consolidate the quantity on the license plate already at the location.
    - **Group put away** – Set to *Yes* to group the putaway work. This option is available when work is grouped either by the worker or by the system. When the worker has finished all the picking work in the group, putaway work is created for the same group.
    - **Audit template ID** – Select the work audit template that will interrupt the work process for this menu item so that another operation can be performed. For example, if this menu item is for inbound work, the audit template might require that the worker checks the temperature in the delivery container. The point at which the process is interrupted is specified on the audit template and can be, for example, when work is started or completed, or when its status changes.
    - **Full LP movement policy** – This field can help make workers more efficient when they move full license plates. The best value depends on how you manage your warehouse movements. Select one of the following options:

        - *Use specification for single item movement* – The worker is prompted to specify all relevant details (such as quantities) before they move a selected license plate.
        - *Automatically move full LP for single item LP* – If a license plate contains a single item, the worker isn't prompted to scan that item before they move the license plate. However, if a license plate contains multiple items, the worker is prompted to scan each item after they identify the license plate.
        - *Automatically move full LP* – The system assumes that all warehouse movements are for entire license plates, regardless of the number items that a license plate contains. The worker is never prompted to scan the items. This option works well when, for example, all warehouse movements are for entire pallets.

1. On the Action Pane, select **Save**.
1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu**, and add the new mobile device menu item to the appropriate new or existing menu.
