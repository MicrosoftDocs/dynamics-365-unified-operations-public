---
title: License plate build on the warehouse app
description: Learn about the License plate build menu item and how it can streamline warehouse operations by nesting license plates.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 02/19/2025
ms.custom:
ms.reviewer: kamaybac
ms.search.form:  LicensePlate. WHSWorker
---

# License plate build on the warehouse app

[!include [banner](../includes/banner.md)]

This article explains how to set up the Warehouse Management mobile app to build license plates. A license plate is a unique identifier that is assigned to a group of items. License plates help streamline the process of managing items, because items don't have to be handled individually. Instead, all the items that share a license plate can be tracked as a single unit.


This functionality lets you assign multiple child license plates to a single parent license plate. Therefore, in effect, the license plates become nested. License plate nesting is beneficial because a warehouse worker can move a larger group of inventory in one action. Therefore, the worker's processes are streamlined.


The **License plate build** menu item in the Warehouse Management mobile app helps with this process by letting users select a parent license plate and assign child license plates to it. However, license plate nesting works only if the following conditions are met:


- No on-hand inventory is assigned to the parent license plate. If the license plate that you try to use as a parent has on-hand inventory, you receive an error message.

- Any license plates that have on-hand inventory are the final members of the sequence. If you think of the whole sequence of license plates as a tree, these license plates are the leaves.


## Configure the License plate build menu item


To configure the **License plate build** menu item, follow these steps.


1. In Supply Chain Management, go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.

1. On the Action Pane, select **New**.

1. On the header of the new record, set the following fields:

    - **Menu item name** – Enter a unique name to identify the menu item. For example, enter *License plate building*.

    - **Title** – Enter the title that should be shown on the mobile device menu. The title doesn't have to be unique.

    - **Mode** – Select *Indirect*, because this flow isn't directly related to work.


1. On the **General** FastTab, set the following fields:


    - **Use process guide** – Set this option to *No*, because process guide isn't supported for this flow.

    - **Barcode data policy** – Leave this field blank.

1. On the Action Pane, select **Save**.

To create a standalone menu item that can be used to assign license plates to a parent, follow these steps.



1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu**.
1. Add the new menu item to an appropriate place in your mobile device menu structure.


## Example 

This example shows how a parent license plate can be used to move on-hand inventory.


For this example, the following setup is in place:


- A parent license plate, *LP-PARENT*, has two nested license plates, *LP-CHILD1* and *LP-CHILD2*.

- There are two items, *item-1* and *item-2*.

- Both items have on-hand inventory in the same location, *location-1*.

- In location *location-1*, item *item-1* has on-hand inventory in license plate *LP-CHILD1*. Item *item-2* has on-hand inventory in license plate *LP-CHILD2*.


You want to move the on-hand inventory of items *item-1* and *item-2* to a new location, *new-location*. Therefore, you create an inventory movement on the parent license plate, *LP-PARENT*. By moving the parent license plate, you transfer all the nested on-hand inventory in the sequence of license plates to the new location in a single action.


To verify the on-hand movement, follow these steps.


1. In Supply Chain Management, go to **Inventory and management** \> **Inquiries and reports** \> **On-hand list**.

1. Filter the results by the two items, *item-1* and *item-2*.

1. For each item, select **Quantity adjustment** on the Action Pane. The page shows the on-hand inventory quantity that was put in the new location, *new-location*.


> [!IMPORTANT]

> Parent license plates are intended to serve as links to groups of nested license plates. Therefore, for optimal performance, we recommend that you never assign on-hand inventory to parent license plates. Although some workflows might continue to work if a parent license plate has on-hand inventory, this scenario isn't fully supported.


Learn about parent license plates when advance ship notices (ASNs) are used in [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving).

