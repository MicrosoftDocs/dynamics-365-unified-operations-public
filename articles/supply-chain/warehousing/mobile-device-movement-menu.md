---
title: Set up a mobile device menu item for moving items in the warehouse
description: Learn how to set up a mobile device menu item that lets workers register manual movements of items in the warehouse, including a step-by-step process.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 12/12/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItem
---

# Set up a mobile device menu item for moving items in the warehouse

[!include [banner](../includes/banner.md)]

This article explains how to set up a mobile device menu item that lets workers register manual movements of items in the warehouse. The worker who uses this mobile device menu item decides what to move and where to move it.

Follow these steps to create and configure a mobile device menu item for registering movements in the warehouse.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. On the header of the new record, set the following fields:

    - **Menu item name** – Enter a unique name to identify the menu item.
    - **Title** – The title that you enter will be shown in the user interface (UI). It doesn't have to be unique.
    - **Mode** – Select *Work*. This value is required because this mobile flow involves work.
    - **Use existing work** – Set this option to *No*, because the work is created as the movement is done.

1. On the **General** FastTab, set the following fields:

    - **Work creation process** – Select *Movement*, because this type of work is what the menu item supports. The page is updated to provide settings that are relevant to this type of work.
    - **Display inventory status** – Set this option to *Yes* to show the inventory status on the device. Set it to *No* to use the default inventory status. If the items that are moved have only one inventory status, that status is the default status. If you use only one inventory status, you typically won't have to show this information.
    - **Use default data** – Set this option to *Yes* if you want specific data fields to be shown by default to workers who use the mobile app. Default data field values can provide information that workers typically need in their daily work. After you set this option to *Yes*, select **Default data** on the Action Pane to open a page where you can select the fields to show. For example, the *From location* field is often useful. Set this option to *No* if you don't want to select any default data for the menu item.
    - **Use process guide** – Set this option to *No*, because process guide isn't currently supported for movements of items.
    - **Barcode data policy** – Select the policy to use when multiple fields are filled in based on a single bar code scan. Learn more in [GS1 bar codes](gs1-barcodes.md).
    - **Generate license plate** – Set this option to *Yes* to automatically create new license plates as they're needed. Set it to *No* if the worker must always select an existing license plate. A license plate is needed if part of the quantity is moved from a license plate. A license plate is also needed if the "from" location isn't license plate controlled, but the "to" location is.
    - **Confirm cancel** – Select whether workers should be asked for confirmation when they cancel a movement operation that's in progress. Confirmation adds an extra step but can help prevent loss of information if a worker unintentionally cancels the operation.
    - **Display container type** – Select whether to show the container type in the app. The container type must typically be shown if workers require information about the type of container that the license plate is associated with.
    - **Deferred operation processing policy** – Select one of the following values to specify whether [deferred processing](deferred-processing-manual-inventory-movement.md) should be used for movements that are registered by using this menu item:

        - *Respect settings* – Use deferred operation processing as defined on the work processing policy.
        - *Override settings and process operation synchronously* – Override the setting, and process the operation synchronously. This value allows for configurations where the mobile device processes the movement synchronously, regardless of the configuration for the type.

    - **Full LP movement policy** – This field can help make workers more efficient when they move full license plates. The best value depends on how you manage your warehouse movements. Select one of the following options:

        - *Use specification for single item movement* – The worker is prompted to specify all relevant details (such as quantities) before they move a selected license plate.
        - *Automatically move full LP for single item LP* – If a license plate contains a single item, the worker isn't prompted to scan that item before they move the license plate. However, if a license plate contains multiple items, the worker is prompted to scan each item after they identify the license plate.
        - *Automatically move full LP* – The system assumes that all warehouse movements are for entire license plates, regardless of the number items that a license plate contains. The worker is never prompted to scan the items. This option works well when, for example, all warehouse movements are for entire pallets.

1. On the Action Pane, select **Save**.
1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu**, and add the new mobile device menu item to the appropriate new or existing menu.
