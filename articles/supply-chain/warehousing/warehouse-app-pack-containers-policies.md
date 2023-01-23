---
title: Mobile device container packing policies
description: Mobile device container packing policies let you control the packing process supported by the Warehouse Management mobile app.
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

Mobile device container packing policies let you control the packing process supported by the Warehouse Management mobile app.

For more information about how packing containers with the Warehouse Management mobile app works, see [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md). For an example of how to set up and use this functionality, see [Example scenario – Pack containers with the Warehouse Management mobile app](warehouse-app-pack-containers-scenario.md).

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.32 or later.
- The feature that is named *Pack containers using the Warehouse Management mobile app* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up mobile device container packing policies

Follow these steps to set up your mobile device container packing policies

1. Go to **Warehouse management \> Setup \> Packing \> Mobile device container packing policies**.
1. Do one of the following steps:
    - To create a new policy, select **New** on the Action Pane.
    - To edit an existing policy, select it in the list pane and then select **Edit** on the Action Pane.
    - To delete an existing policy, select it in the list pane and then select **Delete** on the Action Pane.
1. Make the following settings in the header of your new or selected policy:
    - Packing policy ID – Enter a unique name for the policy.
    - Description – Enter a short description of the policy.
1. On the **General** FastTab, make the following settings:
    - **Capture tracking dimensions** – Choose whether the worker must specify tracking dimensions in the *Pack inventory into containers* flow on the warehouse mobile device. Select one of the following options:
        - *Skip capturing* – The worker won't be asked to specify tracking dimensions during packing. However, if serial numbers are used and the tracking dimensions group is set to capture serial at packing, then the worker will be asked to specify the serial number.
        - *Capture one by one* – Tracking dimensions won't be set by default, so the worker will always need to specify them.
    - **Starting step** – Choose the first step to be shown in the *Pack inventory into containers* flow on the warehouse mobile device (shown after the worker signs in to the packing station).
      - *Scan shipment ID first* – The worker will be asked to scan a shipment ID. This option allows workers to pack items from multiple license plates if needed.
      - *Scan license plate ID first* – The worker will be asked to scan the license plate ID. When you use this option, all items to be packed must be found on the specified license plate. If the license plate contains items from multiple shipments, then the worker will be prompted to specify which shipment to pack for.
    - **Item selection** – Choose which items will be packed in the *Pack inventory into containers* flow on the warehouse mobile device.
      - *Select item to pack* – The worker will be asked to scan an item to pack.
      - *Pack all remaining* – The worker will pack items for the specified shipment or license plate into the container. You can't use this option when capturing tracking dimensions.
    - **Close container automatically** – This setting is only available when **Item selection** is set to *Pack all remaining*. Set this option to *Yes* to automatically close the container after packing all the items. The worker won't be able to update the weight before closing the container, so the weight from the item master data will be used.
    - **Create container automatically** – This setting is only available when **Item selection** is set to *Pack all remaining*. Set this option to *Yes* to automatically create a new container at the start of the packing process. For this functionality to work, the following conditions must be in place:
        - On the **Warehouse Management \> Setup \> Worker** page, each relevant worker must have a worker record that has a **Packing profile ID** set.
        - The selected **Packing profile ID** record for each relevant worker must have a **Container type** assigned and the **Container ID mode** must be set to *Auto*.
1. Select **Save** on the Action Pane.

## Assign a container packing policy to a mobile device menu item

For a mobile device container packing policy to take effect, you must assign it to each mobile device menu item where it applies. To do so, follow these steps:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Do one of the following steps:
    - To create a new menu item, select **New** on the Action Pane.
    - To edit an existing menu item, select it in the list pane and then select **Edit** on the Action Pane.
1. Make the following settings in the header of your new or selected menu item:
    - **Menu item name** – Enter unique, internal name for the menu item.
    - **Title** – Enter the display name of the menu item  to be shown in the mobile app.
    - **Mode** – Must be set to *Indirect*.
1. Make the following settings on the **General** FastTab.
    - **Activity code** – Must be set to *Pack inventory into containers*.
    - **Packing policy ID**  – Select the mobile device container packing policy that you want to use with this menu item.

## Additional resources

- [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md)
- [Example scenario – Pack containers with the Warehouse Management mobile app](warehouse-app-pack-containers-scenario.md).