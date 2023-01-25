---
title: Warehouse groups
description: This article describes how to set up and use warehouse groups
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

Warehouse groups let you establish groups of warehouses that you can associate with various other records in Supply Chain Management.

> [!NOTE]
>
> - Each warehouse can be be assigned to any number of warehouse groups.
> - Only warehouses that are enabled for advanced warehouse processes (WMS) can be assigned to warehouse groups.

## Prerequisites

This feature requires Supply Chain Management 10.0.32 or later.

## Create and manage warehouse groups

To create and manage your warehouse groups, follow these steps:

1. Go to **Warehouse management \> Setup \> Warehouse groups**.
1. Do one of the following steps:
    - To create a new group, select **New** on the Action Pane.
    - To edit an existing group, select it in the list pane and then select **Edit** on the Action Pane.
    - To delete an existing group, select it in the list pane and then select **Delete** on the Action Pane.
1. Make the following settings in the header of your new or selected group:
    - **Warehouse group** – Enter a unique name for the group.
    - **Name** – Enter a short description of the group.
1. On the **Warehouses** FastTab, establish the list of warehouses that should be members of the current group.
    - To add a warehouse to the group, select **Add** from the FastTab toolbar to add a new row to the grid. Then select a warehouse in the **Warehouse** column for the new row (only WMS-enabled warehouses are listed). The other column values will update automatically based on the warehouse you choose.
    - To remove a warehouse, select it in the grid, and then select **Remove** from the FastTab toolbar.
    - To replace a warehouse, find the warehouse you want to remove in the grid, and then edit the value in the **Warehouse** column to replace it with the warehouse you want to add instead.

## Use warehouse groups

When you're setting up some types of warehousing features (such as [location directives](create-location-directive.md), [wave templates](wave-templates.md), or [container packing policies](packing-containers.md)), you'll be able to choose whether to apply the feature to a single warehouse, a group of warehouses, or all warehouses. Usually you'll see two fields, one where you choose the warehouse scope (*Warehouse*, *Group*, or *All*), and another where you specify a selection based on that scope (a single warehouse ID, a warehouse group ID, or all warehouses).
