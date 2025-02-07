---
title: React to last-minute changes in production
description: Learn about types of changes that are often made to components or routes just before production orders are released to the shop floor.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 03/21/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# React to last-minute changes in production

[!include [banner](../includes/banner.md)]

Components or routes can often change at the last minute of the manufacturing process, just before production orders are released to the shop floor. This article describes a few types of last-minute changes that often occur and explains how to manage them in Microsoft Dynamics 365 Supply Chain Management.

## Change BOM items on production orders

Sometimes, a bill of materials (BOM) item must be changed on multiple production orders. These changes are common when a change or revision is applied to a raw item. To allow for such changes, you can change one BOM item to another on estimated or scheduled production orders. Alternatively, you can use all the existing on-hand inventory of an item and then substitute a new item for that item.

### Prerequisites to change BOM items on production orders

Before you can change BOM items on production orders, your system must meet the following requirements:

- You must be running Supply Chain Management 10.0.38 or later.
- The feature that's named *Change BOM item* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.41, this feature is turned on by default. As of Supply Chain Management version 10.0.43, it's mandatory and can't be turned off.

### Change a BOM item on a production order

To change a BOM item that's used on any production order, follow these steps.

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select one or more production orders that you want to change. You can change BOM items only for production orders that have a status of *Estimated* or *Scheduled*. (You can't change them for production orders that have a status of *Created*, for example.)
1. On the Action Pane, on the **Production order** tab, in the **Change** group, select **Change BOM item**.
1. In the **Change production order BOM item** dialog box, on the **Parameters** FastTab, in the **From item** section, specify the item that you want to change from. Include the item's inventory dimensions.

    When you enter the **Item number** value for the "from" item, the system looks up all transactions that have a reference of *Production line*. It shows on-hand inventory from the net requirement for the "from" item. The goal is to easily replace one item with another on the BOM of an item that's being produced.

1. In the **To item** section, specify the item that you want to change to. Include the item's inventory dimensions.

    - The "to" item must use the same inventory unit of measure as the "from" item.
    - If the new item requires a different quantity, specify the new quantity in the **New quantity** field.
    - If the **New quantity** field is set to *0* (zero), the system uses the same quantity as the existing item.

1. The **Production order lines** FastTab shows a list of all the selected production orders that include the specified "from" item on their BOMs. Mark the orders where you want to substitute the specified "to" item for the specified "from" item.
1. A special case occurs when an item must be replaced by a new version or a new product. In this case, you might have to find the time when the on-hand inventory of an item (the "from" item) will be consumed, so that the new item can be swapped in for the production. You'll use the on-hand inventory until it becomes 0 (zero) and then mark all orders so that they use the new item. If this case applies to your current operation, you can select **Proposal to use-up on-hand** on the toolbar of the **Production order lines** FastTab to automatically change the product after its on-hand inventory reaches 0 (in other words, when the accumulated inventory goes negative). In this way, you can see the date when the item will no longer be used, and you can then change the effective dates for the version or item on the BOM.
1. On the **Run in the background** FastTab, either choose to implement the changes right away, or configure settings to control whether and how it runs as a batch job.
1. Select **OK** to apply your settings.

When the change is applied, the system changes the quantity of the BOM line for the "from" item to 0 (zero). It then creates a new BOM line that has the "to" item and the new quantity, and updates the line so that it shows the information for that item. The following fields from the line for the "from" item are copied to the line for the "to" item. Therefore, no manual changes are required.

- Line type
- Vendor
- Site
- Warehouse
- Scrap
- Flushing principle
- Resource consumption
- Per series

## Change production order routes

It's often useful to change the setup times for routes when improvements are made or machines are changed for the same process.

### Prerequisites to change production order routes

Before you can change production order routes, your system must meet the following requirements:

- You must be running Supply Chain Management 10.0.38 or later.
- The feature that's named *Production order route change* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.41, this feature is turned on by default. As of Supply Chain Management version 10.0.43, it's mandatory and can't be turned off.

### Change a production order route

To change a production order route, follow these steps.

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select one or more production orders that you want to change.
1. On the Action Pane, on the **Production order** tab, in the **Change** group, select **Change route**.
1. In the **Production order change route item** dialog box, on the **Parameters** FastTab, specify the "from" route and the "to" route.
1. The **Production order lines** FastTab shows a list of the selected production orders that use the "from" route. Mark the orders where you want to substitute the specified "to" route for the specified "from" route.
1. On the **Run in the background** FastTab, either choose to implement the changes right away, or configure settings to control whether and how it runs as a batch job.
1. Select **OK** to apply your settings.
