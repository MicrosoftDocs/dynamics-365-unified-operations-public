---
title: Set up a mobile device menu item for moving items in the warehouse
description: This article shows how to set up a mobile device menu item that lets workers register manual movements of items in the warehouse. When using this mobile device menu item, the worker decides what to move and where to move it.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/12/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up a mobile device menu item for moving items in the warehouse

[!include [banner](../includes/banner.md)]

This article shows how to set up a mobile device menu item that lets workers register manual movements of items in the warehouse. When using this mobile device menu item, the worker decides what to move and where to move it.

Follow these steps to create and configure a mobile device menu item for registering movements in the warehouse.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, select **New**.
1. Make the following settings in the heading of the new record:
    - **Menu item name** – Enter a unique name so the menu item can be identified.
    - **Title** – This is the text that will be shown in the UI. It doesn't need to be unique.
    - **Mode** – Select *Work*. This setting is needed because this mobile flow involves work.
    - **Use existing work** – Set to *No*. Because the work is being created as the movement is done, this should be set to *No*.

1. Make the following settings on the **General** FastTab:
    - **Work creation process** – Select *Movement*. This is the type of work the current menu item supports. The page updates to provide settings that are relevant for this type of work.
    - **Display inventory status** – Set to *Yes* to display the inventory status on the device. Set to*No* to default the inventory status. If there is only one inventory status of the items being moved, this will be the default status. If you use just one inventory status, you typically won't need to show this information.
    - **Use default data** – Select this option if you'd like to select specific data fields to display to workers using the mobile app. Default data field values can provide information that workers typically need in their daily work. If you set this to *Yes* then select the **Default data** button in the Action Pane to open a page where you can choose which fields to display. For example, the *From location* field is often useful. Set this to*No* if you don't want to select any default data for this menu item.
    - **Use process guide** – Process guide isn't currently supported for movement of items, so set this to *No*.
    - **Barcode data policy** – Choose the policy to use when filling multiple fields based on a single barcode scan. For more information, see [GS1 bar codes](gs1-barcodes.md).
    - **Generate license plate** – Set to *Yes* to automatically create new license plates as needed. Set to *No* if the worker must always choose an existing license plate. A license plate is needed if part of the quantity is being moved from a license plate or if the from-location is not license plate controlled while the to-location is.
    - **Confirm cancel** – Choose whether workers should be asked to confirm when canceling a movement operation in progress. Confirmation adds an extra step, but can help avoid losing information when a worker cancels unintentionally.
    - **Display container type** – Choose whether to display the container type in the app. This is typically needed if workers require information about the type of container that the license plate is associated with.
    - **Deferred operation processing policy** – Choose whether to use [deferred processing for movements](deferred-processing-manual-inventory-movement.md) registered using this menu item. Select one of the following values:
        - *Respect settings* – Use deferred operation processing as defined on the work processing policy.
        - *Override settings and process operation synchronously* – Override the setting and process the operation synchronously. This allows for configurations where the mobile device will process the movement synchronously regardless of the configuration for the type.

    - **Full LP movement policy** – This setting can help make workers more efficient when moving full license plates. The best option to choose depends on how you manage your warehouse movements. Select one of the following options:
        - *Use specification for single item movement* – The worker is asked to specify all relevant details (such as quantities) before moving a selected license plate.
        - *Automatically move full LP for single item LP* – When moving a license plate that contains a single item, the worker isn't asked to scan the item. When moving a license plate with multiple items, the worker is asked to scan each item after identifying the license plate.
        - *Automatically move full LP* – The system assumes all warehouse movements are for entire license plates, regardless of how many items the license plate contains. The worker is never asked to scan the items. This option works well, for example, when all warehouse movements are for entire pallets.

1. On the Action Pane, select **Save**.
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu** and add your new mobile device menu item to the appropriate new or existing menu.
