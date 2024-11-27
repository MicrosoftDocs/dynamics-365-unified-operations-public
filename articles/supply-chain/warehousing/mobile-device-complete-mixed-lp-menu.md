---
title: Set up a mobile device menu item for completing mixed license plates
description: Learn how to set up a mobile device menu item that helps streamline warehouse operations by letting workers continue to process an incoming shipment.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 03/19/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItem
---

# Set up a mobile device menu item for completing mixed license plates

[!include [banner](../includes/banner.md)]

This article explains how to set up the *Complete mixed license plate* mobile device flow. This flow helps streamline warehouse operations by letting workers continue to process an incoming shipment immediately after they register its arrival.

Mixed license plate receiving helps warehouse managers achieve these goals:

- **Increase efficiency and accuracy.** Workers can receive various items onto a single license plate before they register and create putaway work.
- **Handle inbound license plates.** The inbound process is simplified because multiple lines/items can be handled simultaneously.
- **Optimize workflows.** The system can be configured to create work records for each registration. Alternatively, the license plate receiving and putaway process can be used as a single operation.

You can add this capability directly to the mobile device menu, so that workers can run the flow by itself. Alternatively, you can set up a *detour* to make the flow available immediately after a related flow (such as the flow for receiving a purchase order or sales return). A detour is a menu item that can be opened from a step in a main task. Detours let workers "park" the current task, perform another task, and then return to the original task without losing any information.

## Prerequisites

To use the features describe in this article, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.

## Create a mobile device menu item for completing mixed license plates

Follow these steps to create a mobile device menu item that runs the *Complete mixed license plate* mobile device flow.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. On the header of the new record, set the following fields:

    - **Menu item name** – Enter a unique name to identify the menu item (for example, *Complete mixed license plate*).
    - **Title** – Enter the title that should be shown on the mobile device menu. The title doesn't have to be unique.
    - **Mode** – Select *Indirect*. This value is required because this flow isn't directly related to work.
    - **Use existing work** – Set this option to *No* because this flow creates new work when the movement is done.

1. On the **General** FastTab, set the following fields:

    - **Activity Code** – Select *Complete mixed license plate*.
    - **Barcode data policy** – Leave this field blank.

1. On the Action Pane, select **Save**.
1. Follow one of these steps:

    - To create a standalone menu item that workers can use to complete any existing license plate: Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu**, and add the new menu item to an appropriate place in your mobile device menu structure.
    - To add the capability to complete a license plate as part of a larger, existing flow (such as the flow for sales returns): Add the new menu item as a detour of the existing flow. For instructions, see [Configure detours for steps in mobile device menu items](warehouse-app-detours.md).

## Related information

- For information about how to receive shipments by using mixed license plates, see [Mixed license plate receiving](mixed-license-plate-receiving.md).
- For information about to manage return orders, see [Receive unannounced sales returns](sales-returns-unannounced.md).
