---
title: Warehouse groups
description: This article describes how to set up and use warehouse groups.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WhsWarehouseGroup
ms.topic: how-to
ms.date: 01/25/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse groups

Warehouse groups let you establish groups of warehouses that you can associate with various other records in Microsoft Dynamics 365 Supply Chain Management.

> [!NOTE]
>
> - Each warehouse can be assigned to any number of warehouse groups.
> - Only warehouses that are enabled for advanced warehouse processes (WMS) can be assigned to warehouse groups.

## Prerequisites

This feature requires Supply Chain Management version 10.0.32 or later.

## Create and manage warehouse groups

To create and manage your warehouse groups, follow these steps.

1. Go to **Warehouse management \> Setup \> Warehouse groups**.
1. Follow one of these steps:

    - To create a new group, select **New** on the Action Pane.
    - To edit an existing group, select it in the list pane, and then select **Edit** on the Action Pane.
    - To delete an existing group, select it in the list pane, and then select **Delete** on the Action Pane.

1. If you're creating or editing a warehouse group, set the following fields on the header of the new or selected group:

    - **Warehouse group** – Enter a unique name for the group.
    - **Name** – Enter a short description of the group.

1. On the **Warehouses** FastTab, define the list of warehouses that should be members of the current group.

    - To add a warehouse to the group, select **Add** on the FastTab toolbar to add a new row to the grid. Then, in the **Warehouse** column for the new row, select a warehouse. (Only WMS-enabled warehouses are available for selection.) The other column values will be updated automatically, based on the warehouse that you selected.
    - To remove a warehouse from the group, select it in the grid, and then select **Remove** on the FastTab toolbar.
    - To replace one warehouse in the group with another warehouse, find the warehouse that you want to replace in the grid. Then, in the **Warehouse** column, select the warehouse that you want to use instead.

## Use warehouse groups

When you're setting up some types of warehousing features (such as [location directives](create-location-directive.md), [wave templates](wave-templates.md), [outbound sorting templates](outbound-sorting.md), [cross docking templates](planned-cross-docking.md), [slotting templates](warehouse-slotting.md) or [container packing policies](packing-containers.md)), you can specify whether the feature applies to a single warehouse, a group of warehouses, or all warehouses. Usually, you'll see two fields: one where you select the warehouse scope (*Warehouse*, *Group*, or *All*) and one where you make a selection, based on that scope (a single warehouse ID, a warehouse group ID, or all warehouses).
