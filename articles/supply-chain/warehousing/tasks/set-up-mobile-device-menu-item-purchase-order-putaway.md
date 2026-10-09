---
title: Set up a mobile device menu item to complete purchase order putaway work
description: Learn how to set up a mobile device menu item that workers use to complete the putaway work that's created when purchase order receipts are registered.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSRFMenuItem, WHSRFAutoConfirm, WHSRFMenu
ms.topic: how-to
ms.date: 10/09/2026
ms.custom:
  - bap-template
---

# Set up a mobile device menu item to complete purchase order putaway work

[!INCLUDE [banner](../../includes/banner.md)]

When a warehouse worker registers a purchase order receipt, Supply Chain Management creates putaway work that moves the received items from the receiving dock into storage. This article shows how to create the mobile device menu item that a second worker uses to complete that putaway work.

The menu item processes work that already exists, rather than creating new work. It's grouped by work pool, so a worker scans a work pool ID and then receives all the open work in that pool that matches the work classes you assign to the menu item. Learn how to create the menu item that generates the work in the first place in [Set up a mobile device menu item to register received items](set-up-mobile-device-menu-item-register-received-items.md).

Warehouse managers typically perform this task.

## Create the menu item

The menu item defines which work a worker can process and how the system groups and confirms that work. To create the menu item, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. On the Action Pane, select **New**. Then set the following fields for the new menu item:

    - **Menu item name** – Enter a unique identifier, such as *POMove*. This value is internal, and workers don't see it. Make a note of it because you need it when you add the menu item to a menu.
    - **Title** – Enter the text that workers see on the mobile device, such as *PO Move*.
    - **Mode** – Select *Work*.
    - **Use existing work** – Set this option to *Yes*. The system creates the putaway work when you register the receipt, so this menu item processes the existing work instead of creating more.

1. In the **Directed by** field, select *System grouping*. This value directs the system to group the open work for the worker based on a field that the worker scans. The value that you select in this field controls which of the remaining fields appear on the **General** FastTab. To Learn about the other available values in [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md#configure-menu-items-to-process-existing-work).
1. Set the two fields that *System grouping* requires:

    - **System grouping field** – Select *WorkPoolId*. This setting prompts the system to ask workers to scan a work pool ID. The worker then receives all open work lines that both belong to that work pool and use one of the work classes assigned to this menu item.
    - **System grouping label** – Enter the prompt text that workers see on the mobile device, such as *Work pool*.

1. Set the following options to control how workers complete the putaway:

    - **Override license plate during put** – Set this option to *Yes* to let workers put items onto a license plate other than the suggested one when the put location is license plate controlled. This option is useful when a worker consolidates items onto a license plate that's already at the location.
    - **Group put away** – Set this option to *Yes* to combine the putaway instructions for a group of work. When every put line in the group targets the same location, the worker receives one combined put instruction instead of one per line.

1. On the **Work classes** FastTab, select **New**, and then set the **Work class ID** field to *Purchase*. Work classes restrict the work that the menu item can process. In this case, the menu item handles only open work lines that use the *Purchase* work class.
1. On the Action Pane, select **Save**.

The **Mobile device menu items** page offers many more options than the ones covered in this article, including work audit templates and inventory status display. Learn more in [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md#menu-options).

## Set up work confirmation

Work confirmations control which steps a worker must acknowledge and which steps the system completes silently. For this menu item, the pick step is confirmed automatically because the items are already on the license plate that the worker is moving. The put step requires a location scan to ensure that items aren't stored in the wrong place. To set up these confirmations, follow these steps:

1. On the **Mobile device menu items** page, select the menu item that you created. Then, on the Action Pane, select **Work confirmation setup**.
1. Select **New** and then set the **Work type** field to *Pick*.
1. Select the **Auto confirm** check box. Supply Chain Management then confirms the pick instruction automatically, and workers never see it.
1. Select **New** again, and then set the **Work type** field to *Put*.
1. Select the **Location confirmation** check box. Workers must then scan the put location before they can complete the work.
1. On the Action Pane, select **Save**.

Confirmations are available for other work types, such as counting and adjustments, and you can also require product or quantity confirmation. Learn more in [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md#require-workers-to-confirm-the-product-location-or-quantity-when-they-pick-items).

> [!NOTE]
> You can't combine automatic confirmation with location or quantity confirmation for the same work type.

## Add the menu item to a mobile device menu

A new menu item isn't available in the app until you add it to a menu. Workers see only the menu that's assigned to their [mobile device user account](../mobile-device-work-users.md), together with its submenus. To add the menu item to a menu, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu**.
1. In the list pane, select the menu that should include the new menu item, such as your inbound menu. Then, on the Action Pane, select **Edit**.
1. In the **Available menus and menu items** column, select the menu item that you created. Then select the right arrow button to move it to the **Menu structure** column.
1. Use the up arrow and down arrow buttons to position the menu item in the structure.
1. On the Action Pane, select **Save**.

Learn more about building menu structures in [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md#mobile-device-menu).

## Related information

- [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md)
- [Set up a mobile device menu item to register received items](set-up-mobile-device-menu-item-register-received-items.md)
- [Mobile device user accounts](../mobile-device-work-users.md)
- [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md)
- [System grouping on an open work list](../system-group-on-open-work-list.md)
