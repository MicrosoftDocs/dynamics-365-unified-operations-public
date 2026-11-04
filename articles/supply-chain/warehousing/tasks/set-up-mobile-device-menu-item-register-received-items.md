---
title: Set up a mobile device menu item to register received items
description: Learn how to set up a mobile device menu item that warehouse workers use to register the receipt of items that were ordered on a purchase order.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSRFMenuItem, WHSRFMenu, WHSRFDefaultData
ms.topic: how-to
ms.date: 11/04/2026
ms.custom:
  - bap-template
---

# Set up a mobile device menu item to register received items

[!INCLUDE [banner](../../includes/banner.md)]

Warehouse workers use mobile device menu items to run warehouse processes from the Warehouse Management mobile app. This article shows how to create a menu item that workers use to register the receipt of items ordered on a purchase order, and then add that menu item to a menu so that workers can reach it.

The menu item that you create here uses the *Purchase order item receiving* work creation process. A worker identifies the purchase order line by scanning the purchase order number and the item number, and then registers the received quantity. Supply Chain Management creates putaway work that moves the items from the receiving dock into storage. Because that work is created only after the items are registered, a second worker can pick it up and complete the putaway.

Warehouse managers typically perform this task.

## Create the menu item

The menu item defines what the process does and which fields workers see in the app. To create it, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. On the Action Pane, select **New**. Then set the following fields for the new menu item:

    - **Menu item name** – Enter a unique identifier for the menu item, such as *My PO registration*. This value is internal, and workers don't see it.
    - **Title** – Enter the text that workers see on the mobile device, such as *PO registration*. Keep it short because mobile device screens are narrow.
    - **Mode** – Select *Work*. This value indicates that the menu item creates warehouse work.
    - **Use existing work** – Set this option to *No*. The putaway work doesn't exist until the worker registers the received items, so there's no existing work for the menu item to process.

1. In the **Work creation process** field, select *Purchase order item receiving*. The value that you select here determines which of the remaining fields on the **General** FastTab are available because each work creation process supports a different set of options.
1. Set the remaining fields on the **General** FastTab to match how your warehouse receives purchase orders. The following fields are available for this work creation process:

    - **Use default data** – Set this option to *Yes* to make the **Default data** command available on the Action Pane. You can then choose fields that are prefilled for workers, such as a receiving location, which saves keystrokes when workers repeat the same receipt.
    - **Use process guide** – Set this option to *Yes* to run the menu item by using the process guide framework when it's available.
    - **Barcode data policy** – Select a policy if workers scan GS1 bar codes or QR codes that fill several fields from a single scan. Learn more in [GS1 bar codes and QR codes](../gs1-barcodes.md).
    - **License plate grouping policy** – Select how received items are grouped onto license plates:
        - *None* – All items that are received in a single registration go onto one license plate.
        - *License plate grouping* – Items are split across license plates according to the license plate grouping settings on the unit sequence group that's assigned to the item. For example, you can have the system create a separate license plate for each pallet. Learn more in [Set up unit sequence groups](../unit-measure-stocking-policies.md).
        - *User defined* – Items are split according to the quantity and unit that the worker enters. For example, if the worker receives four pallets, the system creates four license plates that each hold one pallet. The quantity must be a whole number.
    - **Generate license plate** – Set this option to *Yes* to have Supply Chain Management create license plate numbers automatically, based on the number sequence for license plates. Set it to *No* if workers scan a license plate that's already labeled, such as one that a vendor applied.
    - **Work template** – Select the work template that creates the putaway work. Leave this field blank to have the system select a template by matching the receipt against the query criteria on each template. If you change the **Work creation process** field later, this field is cleared.
    - **Display disposition code** – Set this option to *Yes* to prompt workers for a disposition code during receiving. Workers can then record the condition of the received items, and the code determines the inventory status and the location directive that apply to the work that's created. Learn more in [Set up mobile device disposition codes](set-up-dispositions-codes.md).
    - **Display batch disposition code** – Set this option to *Yes* to prompt workers for a batch disposition code. If you set it to *No*, batches use the default batch disposition code from the item model group, or the code that's already assigned to the batch. This field is available only when shelf life management is turned on in your system.
    - **Print label** – Set this option to *Yes* to print a license plate label after all the steps in the work template are completed. If the menu item uses a deferred receiving policy, that policy controls label printing instead.
    - **Block receiving with ASN item information** – Set this option to *Yes* to prevent workers from using this menu item to receive purchase orders that have advance shipping notice (ASN) information. Use license plate receiving for those receipts instead.
    - **Display container type** – Set this option to *Yes* to show the container type field on the mobile device. Learn more in [Manage inbound putaway based on container types](../inbound-putaway-by-container-type.md).
    - **Generate catch weight tag** – Set this option to *Yes* to create catch weight tags automatically. This field is available only when catch weight functionality is turned on. Learn more in [Catch weight product processing with warehouse management](../catch-weight-processing.md).
    - **Assign putaway cluster** – Set this option to *Yes* to assign a putaway cluster profile to received inventory. Learn more in [Putaway clusters](../putaway-clusters.md).
    - **Deferred receiving policy ID** – Select a deferred receiving policy to process the inventory on-hand update and the putaway work creation in the background, so that workers can continue receiving without waiting. Learn more in [Mixed license plate receiving](../mixed-license-plate-receiving.md#deferred-receiving-processing).

1. On the Action Pane, select **Save**.

Other work creation processes use different fields on the **General** FastTab. For a description of every option, and of the other available work creation processes, learn more in [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md).

## Add the menu item to a mobile device menu

A new menu item isn't available in the app until you add it to a menu. Workers see only the menu that's assigned to their [mobile device user account](../mobile-device-work-users.md), together with its submenus. To add the menu item to a menu, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu**.
1. In the list pane, select the menu that should include the new menu item, such as your inbound menu. Then, on the Action Pane, select **Edit**.
1. In the **Available menus and menu items** column, select the menu item that you created. Then select the right arrow button to move it to the **Menu structure** column.
1. Use the up arrow and down arrow buttons to position the menu item in the structure.
1. On the Action Pane, select **Save**.

Learn more about building menu structures, including how to hide items that workers reach only as detours, in [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md#mobile-device-menu).

## Related information

- [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md)
- [Set up a mobile device menu item to complete purchase order putaway work](set-up-mobile-device-menu-item-purchase-order-putaway.md)
- [Set up mobile device disposition codes](set-up-dispositions-codes.md)
- [Mobile device user accounts](../mobile-device-work-users.md)
- [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md)
