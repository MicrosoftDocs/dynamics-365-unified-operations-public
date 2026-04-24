---
title: Maintenance request lifecycle states
description: Learn how to set up maintenance request lifecycle states in Asset Management, including a process for setting up maintenance request lifecycle states.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetRequestLifecycleState, EntAssetRequestLifecycleModel
ms.topic: how-to
ms.date: 07/30/2025
ms.custom:
  - bap-template
---

# Maintenance request lifecycle states

[!include [banner](../../includes/banner.md)]

Maintenance request lifecycle states define the stages that a request can go through. Examples include *Created*, *Active*, and *Ended*. When a maintenance request is converted to a work order, the maintenance request lifecycle state should be updated to *Ended* or *Closed* to indicate that the maintenance request is no longer active. On the **All maintenance requests** list page, you can view all maintenance requests, regardless of their lifecycle state.

## Turn the depot repair option on or off

*Depot repair* is a maintenance request type that lets you receive assets from another location so that you can do a maintenance or repair job, and then return the asset after the job is completed. To use depot repair, you must enable its configuration key by following these steps:

1. Put your system into maintenance mode, as described in [Maintenance mode](../../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration** \> **Setup** \> **License configuration**.
1. On the **Configuration keys** tab, expand the **Asset management** node and then select the check box for **Inbound/outbound**.
1. Turn off maintenance mode, as described in [Maintenance mode](../../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

## Manage maintenance request lifecycle states

To manage the maintenance request lifecycle states that you need, follow these steps:

1. Go to **Asset management** \> **Setup** \> **Maintenance requests** \> **Lifecycle states**.
    :::image type="content" source="media/02-setup-for-requests.png" alt-text="Screenshot of the Maintenance request lifecycle states page." lightbox="media/02-setup-for-requests.png":::

1. Use the buttons on the Action Pane to add, remove, or edit a lifecycle state.
1. Make the following settings in the header of your new or selected lifecycle state:
    - **Lifecycle state** – Enter an ID for the lifecycle state.
    - **Name** – Enter a name for the lifecycle state.
1. For existing lifecycle states, the **Lifecycle models** field on the **Details** FastTab shows the number of maintenance request lifecycle models that use this lifecycle state.
1. Set the following options on the **General** FastTab:
    - **Active** – Choose whether a maintenance request should be active while it's in this lifecycle state.
    - **Set actual end** – Choose whether an actual end date and time should automatically be entered on a maintenance request that's in this lifecycle state.
    - **Delete open schedule lines** – Choose whether all maintenance schedule lines without a work order reference should be deleted automatically on a maintenance request that's in this lifecycle state.
    - **Create work order** – Choose whether a work order can be created from a maintenance request that's in this lifecycle state.
    - **Delete** – Choose whether a maintenance request can be deleted while it's in this lifecycle state.

1. If you use depot repair, then the **Update** FastTab is shown. Make the following settings here:
    - **Inbound** – Choose whether the asset lifecycle state of assets that are selected on a maintenance request should automatically be updated to **Inbound** when the maintenance request lifecycle state of that maintenance request is set to **Inbound**.
    - **Outbound** – Choose whether the asset lifecycle state of assets that are selected on a maintenance request should automatically be updated to **Outbound** when the maintenance request lifecycle state of that maintenance request is set to **Outbound**.

> [!NOTE]
> Maintenance request lifecycle states, lifecycle state groups, and lifecycle state types are related to, and used in the same way as, work order lifecycle states, lifecycle state groups, and lifecycle state types.

## Set up maintenance request lifecycle models

After you've created the lifecycle states that are required for your maintenance requests, they can be divided into lifecycle state groups, or lifecycle models. Maintenance request lifecycle models are used to create the flow that can be used for different types of maintenance requests. At a minimum, one standard maintenance request lifecycle model should be created.

1. Go to **Asset management** \> **Setup** \> **Maintenance requests** \> **Lifecycle models**.
    :::image type="content" source="media/06-setup-for-requests.png" alt-text="Screenshot of the Maintenance request lifecycle models page." lightbox="media/06-setup-for-requests.png":::

1. Use the buttons on the Action Pane to add, remove, or edit a lifecycle model.
1. Make the following settings in the header of your new or selected lifecycle model:
    - **Lifecycle model** – Enter an ID for the lifecycle model.
    - **Name** – Enter a name for the lifecycle model.

1. For existing lifecycle models, the **Details** FastTab displays the following information:
    - **Lifecycle states** – Shows the number of lifecycle states that are selected in this lifecycle model.
    - **Maintenance request types** – Shows the number of maintenance request types that use this lifecycle model.

1. On the **Lifecycle states** FastTab, move all of the lifecycle states that should be included in this lifecycle model into the **Lifecycle states selected** column.
    - Use the buttons between the columns to move one or more selected lifecycle states from one column to the other.
    - When a user changes the lifecycle state of a maintenance request, the states are displayed in the order shown in the **Lifecycle states selected** column, which should indicate the way maintenance requests typically progress from start to finish. Use the up and down buttons next to the **Lifecycle states selected** column to adjust the order of the lifecycle states.

1. If you use depot repair, then the **General** FastTab is shown. Make the following settings here:
    - **Lifecycle state for asset received** – Select the asset lifecycle state that assets selected on a maintenance request should automatically be updated to when they're received for depot repair.
    - **Lifecycle state for asset delivered** – Select the lifecycle state that assets selected on a maintenance request should automatically be updated to when they're returned after depot repair.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
