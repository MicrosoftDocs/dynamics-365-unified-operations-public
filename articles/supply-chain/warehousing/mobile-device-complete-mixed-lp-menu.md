---
title: Set up a mobile device menu item for completing mixed license plates
description: This article explains how to set up a mobile device menu item that helps streamline warehouse operations by empowering workers to continue processing an incoming shipment right after registering its arrival.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItem
ms.topic: how-to
ms.date: 03/18/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up a mobile device menu item for completing mixed license plates

[!include [banner](../includes/banner.md)]

This article explains how to set up the *Complete mixed license plate* mobile device flow, which helps streamline warehouse operations by empowering workers to continue processing an incoming shipment right after registering its arrival.

Mixed license plate receiving enables warehouse managers to:

- **Increase efficiency and accuracy** – Let workers receive various items onto a single license plate before registering and creating putaway work.
- **Handle inbound license plates** – Simplify the inbound process by allowing multiple lines/items to be handled simultaneously.
- **Optimize workflows** – Configure the system to create work records for each registration or use the license plate receiving and put-away process as a single operation.

You might choose to add this capability directly to the mobile device menu (where workers could run the flow by itself) or set up a *detour* to make the flow available immediately after a related flow (such as receiving a purchase order or sales return). A detour is a menu item that can be opened from a step in a main task so that workers can "park" the current task, perform another task, and then return to the original task without losing any information.

## Create a mobile device menu item for completing mixed license plates

Follow these steps to create a mobile device menu item that runs the *Complete mixed license plate* mobile device flow.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. On the header of the new record, set the following fields:
    - **Menu item name** – Enter a unique name in the field to identify the menu item (for example, *Complete mixed license plate*).
    - **Title** – Enter a title as it should be shown in the mobile device menu. It doesn't have to be unique.
    - **Mode** – Select *Indirect*. This value is required because this flow isn't directly related to work.
    - **Use existing work** – Set this option to *No* because this flow creates new work when the movement is done.

1. On the **General** FastTab, set the following fields:

    - **Activity Code** – Select *Complete mixed license plate*.
    - **Barcode data policy** – Leave blank.

1. On the Action Pane, select **Save**.

1. Do one of the following steps:
    - To create a stand-alone menu items that workers can use to complete any existing license plate, go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu** and add the new menu item to an appropriate place in your mobile device menu structure.
    - To add the ability to complete a license plate as part of a larger, existing flow (such as for sales returns), then add this menu item as a detour of the existing flow. For instructions, see [Configure detours for steps in mobile device menu items](warehouse-app-detours#enable-detours-in-your-system).

## Additional resources

- For information about how to receive shipments using mixed license plates, see [Mixed license plate receiving](mixed-license-plate-receiving.md).
- For more information about to manage return orders, see [Receive unannounced sales returns](sales-returns-unannounced.md).
