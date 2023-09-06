---
title: Mobile device container packing policies
description: This article provides information about mobile device container packing policies, which let you control the packing process that's supported by the Warehouse Management mobile app.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/30/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Mobile device container packing policies

Mobile device container packing policies let you control the packing process that's supported by the Warehouse Management mobile app.

For more information about how packing containers work with the Warehouse Management mobile app, see [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md). For an example that shows how to set up and use this functionality, see [Example scenario – Pack containers with the Warehouse Management mobile app](warehouse-app-pack-containers-scenario.md).

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.32 or later.
- The feature that's named *Pack containers using the Warehouse Management mobile app* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.36, this feature is turned on by default.

## Set up mobile device container packing policies

Follow these steps to set up your mobile device container packing policies.

1. Go to **Warehouse management \> Setup \> Packing \> Mobile device container packing policies**.
1. Follow one of these steps:

    - To create a new policy, select **New** on the Action Pane.
    - To edit an existing policy, select it in the list pane, and then select **Edit** on the Action Pane.
    - To delete an existing policy, select it in the list pane, and then select **Delete** on the Action Pane.

1. If you're creating or editing a policy, on the header of the new or selected policy, set the following fields:

    - **Packing policy ID** – Enter a unique name for the policy.
    - **Description** – Enter a short description of the policy.

1. On the **General** FastTab, set the following fields:

    - **Capture tracking dimensions** – Select one of the following options to indicate whether the worker must specify tracking dimensions in the *Pack inventory into containers* flow on the warehouse mobile device:

        - *Skip capturing* – The worker won't be asked to specify tracking dimensions during packing. However, if serial numbers are used, and the tracking dimensions group is set to capture serial numbers at packing, the worker will be asked to specify the serial number.
        - *Capture one by one* – Tracking dimensions won't be set by default. Therefore, the worker will always have to specify them.

    - **Starting step** – Select the first step that's shown in the *Pack inventory into containers* flow on the warehouse mobile device. (The step will be shown after the worker signs in to the packing station.)

        - *Scan shipment ID first* – The worker will be asked to scan a shipment ID. This option enables workers to pack items from multiple license plates as required.
        - *Scan license plate ID first* – The worker will be asked to scan the license plate ID. When you use this option, all items that will be packed must be found on the specified license plate. If the license plate contains items from multiple shipments, the worker will be prompted to specify which shipment to pack for.

    - **Item selection** – Select which items will be packed in the *Pack inventory into containers* flow on the warehouse mobile device:

        - *Select item to pack* – The worker will be asked to scan an item to pack.
        - *Pack all remaining* – The worker will pack items for the specified shipment or license plate into the container. You can't use this option when tracking dimensions are captured.

    - **Close container automatically** – This option is available only when the **Item selection** field is set to *Pack all remaining*. Set it to *Yes* to automatically close the container after all the items are packed. Because the worker won't be able to update the weight before they close the container, the weight from the item master data will be used.
    - **Create container automatically** – This option is available only when the **Item selection** field is set to *Pack all remaining*. Set it to *Yes* to automatically create a new container at the start of the packing process. For this functionality to work, the following conditions must be met:

        - On the **Worker** page (**Warehouse Management \> Setup \> Worker**), in the worker record for each relevant worker, the **Packing profile ID** field must be set.
        - In the selected **Packing profile ID** record for each relevant worker, a **Container type** value must be assigned, and the **Container ID mode** field must be set to *Auto*.

1. On the Action Pane, select **Save**.

## Assign a container packing policy to a mobile device menu item

For a mobile device container packing policy to take effect, you must assign it to each mobile device menu item where it applies. Follow these steps to assign a container packing policy a menu item.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Follow one of these steps:

    - To create a new menu item, select **New** on the Action Pane.
    - To edit an existing menu item, select it in the list pane, and then select **Edit** on the Action Pane.

1. On the header of the new or selected menu item, set the following fields:

    - **Menu item name** – Enter a unique internal name for the menu item.
    - **Title** – Enter the display name that will be shown for the menu item in the mobile app.
    - **Mode** – This field must be set to *Indirect*.

1. On the **General** FastTab, set the following fields:

    - **Activity code** – This field must be set to *Pack inventory into containers*.
    - **Packing policy ID** – Select the mobile device container packing policy to use with the menu item.

## Additional resources

- [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md)
- [Example scenario – Pack containers with the Warehouse Management mobile app](warehouse-app-pack-containers-scenario.md)
