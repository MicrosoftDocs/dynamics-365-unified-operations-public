---
title: License plate build via the Warehouse Management mobile app
description: Learn about the License plate build menu item and how it can streamline warehouse operations by nesting license plates.
author: Atapiabailon
ms.author: atapiabailon
ms.topic: article
ms.date: 18/02/2025
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  LicensePlate. WHSWorker
---

# License plate build via the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article explains how to set up the Warehouse Management mobile app so that it supports using license plate building, complemented with an example scenario.

> [!NOTE]
> #### What is a License plate?
> A license plate is a unique identifier assigned to a group of items, streamlining the process of managing them. Instead of handling each item individually, a license plate enables tracking them as a single unit.

This functionality allows you to assign multiple license plates to a single parent license plate, effectively nesting them. The advantage of nesting license plates is that it enables the movement of a larger group of inventory in one go, streamlining the warehouse worker's processes.

This process can be achieved by using the mobile device menu item called **License plate build**.

The **License plate build** menu item allows users to choose a parent license plate and assign child license plates to it. This action should be performed from the warehouse management mobile application. There are a couple of conditions that need to be met in order for the nesting of license plates to work:

1. The parent license plate should not have any on-hand inventory assigned to it. If you try to use a license plate with on-hand inventory as a parent, the system will display an error message.
1. The license plates with on-hand inventory should be the final members of the sequence, similar to the leaves of a tree.

## Configure the License plate build menu item

To configure the **License plate build** menu item, follow these steps:

1. Navigate to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the action pane, click on **New**.
1. On the header of the new record, set the following fields:

    - **Menu item name** – Enter a unique name to identify the menu item (for example, *License plate building*).
    - **Title** – Enter the title that should be shown on the mobile device menu. The title doesn't have to be unique.
    - **Mode** – Select *Indirect*. This value is required because this flow isn't directly related to a work.

1. On the **General** FastTab:

    - **Use process guide** – Process guide is not yet supported for this flow.
    - **Barcode data policy** – Leave this field blank.

1. On the Action Pane, select **Save**.
1. To create a standalone menu item that workers can use to assign license plates to a parent: Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu**, and add the new menu item to an appropriate place in your mobile device menu structure.

## Example of moving on-Hand inventory using a parent license plate

Consider the following scenario:
1. A parent license plate, *LP-PARENT*, with nested license plates *LP-CHILD1* and *LP-CHILD2*.
1. Two items, *item-1* and *item-2*.
1. The two items have on-hand inventory in *location-1* and license plates *LP-CHILD* and *LP-CHILD2* respectively.

If you want to move the on-hand inventory of the items *item-1* and *item-2* to a new location, *new-location*, you should perform an inventory movement on the parent license plate, *LP-PARENT*. By moving the parent license plate, all the nested on-hand inventory within the sequence of license plates will be transferred to the new location in a single action.

To verify the on-hand movement, in Supply Chain Management:
1. Navigate to **Inventory and management** \> **Inquiries and reports** \> **On-hand list**.
1. Filter the results by the two items, *item-1* and *item-2*.
1. For each item, click **Quantity adjustment** on the action pane.
1. You will see the on-hand inventory placed in the new location, *new-location*.

> [!IMPORTANT]
>
> Remember that parent license plates should never have on-hand inventory assigned to them, as they are intended to serve as links to groups of nested license plates.
>
> If you end up with a parent license plate that has on-hand inventory, there are various workflows that may still function, but this scenario is not fully supported by the system.
>
> For optimal performance, it is recommended to never assign on-hand inventory to parent license plates.

## Related information
- For information about the behavior of parent license plates when using ASN, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving).



