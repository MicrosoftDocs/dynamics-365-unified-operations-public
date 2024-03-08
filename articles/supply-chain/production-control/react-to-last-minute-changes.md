---
title: React to last minute changes in production
description: Components or routes can often change at the list minute of the manufacturing process, just before production orders are released to the shop floor. This article describes a few types of changes that often occur and how to react to manage them in Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/08/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# React to last minute changes in production

[!include [banner](../includes/banner.md)]

Components or routes can often change at the last minute of the manufacturing process, just before production orders are released to the shop floor. This article describes a few types of changes that often occur and how to manage them in Supply Chain Management.

## Change BOM items on production orders  

It can sometimes be necessary to change a bill of material (BOM) item on multiple production orders. Such changes are common when a change of revision is applied to a raw item. To allow for such changes, you can change one BOM item to another in estimated or scheduled production orders. You can also choose to use up the existing on-hand inventory of an item and then substitute it for a new one once that inventory has been used.

### Prerequisites to change BOM items on production orders

To change BOM items on production orders, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Change BOM item* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Change a production order BOM item

To change a production order BOM item, follow these steps:

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Open the production order that you want to change. You can only change BOM items for production orders with a status of *Estimated* or *Scheduled* (not with status *Created*). <!--KFM: It seems like we have more status values than this.-->
1. On the Action Pane, open the **Production order** tab and, from the **Change** group, select **Change BOM item**.
1. The **Change production order BOM** item dialog opens.
1. On the **Parameters** FastTab, in the **From item** section, specify the item you want to change from, including its inventory dimensions.

    <!--KFM: I didn't see this. I'm not sure what this means. --> When you enter the **From item**, the system looks up all transactions with a reference of *Production line*. The system shows on-hand inventory from the net requirement for the **From item**. The purpose is to easily change an item for another one in the BOM of an item being produced.

1. On the **Parameters** FastTab, in the **To item** section, specify the item you want to change to, including its inventory dimensions. 
    - The **To item** must use the same inventory unit of measure as the **From item**..
    - If the new item demands a different quantity, specify the new quantity in the **New quantity** field.
    - If **New quantity** is set to zero, the system uses the same quantity as the existing item.
1. On the **Production order** lines FastTab, <!-- KFM: What Can we do here? What is this for? -->
1. A special case occurs when an item is to be replaced by a new version or a new product. Here, you might need to find the time when the on-hand inventory of an item (the *from item*) will be consumed so that the new item can be swapped in for the production. You'll use the on-hand inventory until it becomes 0, and thereafter mark all orders to use the new item. Select  **Proposal to use-up on-hand** on the **Production order lines** FastTab toolbar to automatically change the product once its on-hand inventory reaches 0 (in other words, when the accumulated inventory goes negative). This lets you see the date when the item will no longer be used, so the effective dates can be changed for the version or item on the BOM. <!--KFM: I don't really understand this, but maybe it's ok? -->
1. On the **Run in the background** FastTab, choose to implement the changes right away or make settings to control whether and how to run it as a batch job.
1. Select **OK** to apply your settings.

When the change is applied, the system changes the quantity of the **From item** to 0. Then it creates a new line <!--KFM: What kind of line is this? -->with the **To item**, with the new quantity, and updates the line <!--KFM: What line? --> to show the information for this item. The following fields from the *from line* are copied to the *to line* (so no manual changes are needed):

- Line type
- Vendor
- Site
- Warehouse
- Scrap
- Flushing principle
- Resource consumption
- Per series

## Change production order routes

It's often useful to change setup times for routes when improvements are made or machines are changed for the same process.

### Prerequisites to change production order routes

To change production order routes, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Production order route change* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Change a production order route

To change a production order route, follow these steps:

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Open the production order that you want to change.  <!--KFM: Mention status values here?-->
1. On the Action Pane, open the **Production order** tab and, from the **Change** group, select **Change route**.
1. The **Production order change route** item dialog opens.
1. On the **Parameters** FastTab, identify the **From route** and **To route**.
1. On the **Production order lines** FastTab, <!-- KFM: What Can we do here? What is this for? -->
1. On the **Run in the background** FastTab, choose to implement the changes right away or make settings to control whether and how to run it as a batch job.
1. Select **OK** to apply your settings.
