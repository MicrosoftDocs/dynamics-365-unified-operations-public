---
# required metadata

title: Override the default reservation principle for materials in production
description: This topic describes how to set a default reservation principle for each item model group, which lets you can have different reservation principles applied automatically for each item that is part of a production bill of material (BOM) or batch order formula 
author: johanhoffmann
manager: tfehr
ms.date: 12/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2020-12-10
ms.dyn365.ops.version: 10.0.17
---

# Override the default reservation principle for materials in production

[!include [banner](../includes/banner.md)]

The *Override default production reservation* feature enables you to set a default reservation principle for each item model group, which means that you can have different reservation principles applied automatically for each item that is part of a production bill of material (BOM) or batch order formula. For each item model group, you can choose whether that group should override the default reservation principle set for an order, and choose what that group's reservation principle should be instead (manual, estimation, scheduling, release, or start).

When you create a new production or batch order, you are asked to select a reservation principle to apply to that order and all of its BOM or formula lines. With this feature, some or all of the BOM or formula lines can instead override that default to match the reservation principle set for the relevant item model group.

For example, if you have raw materials or ingredients that requires pick work, then BOM or formula lines created for those products will require a physical reservation because that is a prerequisite for generating warehouse work. If you want the reservation to happen automatically, then you will usually choose one of the following reservation principles: *estimation*, *scheduling*, *release* or *start*. On the other hand, if you have materials or ingredients that are consumed directly from a location, and therefore don't require pick work, then you'd typically select the *manual* reservation principle, which doesn't make any physical reservations and won't generate any pick work.

## Turn on the feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module**: *Production control*
- **Feature name**: *Override default production reservation*

## Assign a production reservation policy to an item model group

To assign a production reservation policy to an item model group:

1. Go to **Cost management &gt; Inventory accounting policies setup &gt; Item model groups**.
1. Create or select an item model group.
1. Expand the **Inventory policies** FastTab.
1. Select the **Override item production reservation** check box.
1. From the **Reservation** drop-down list, select one of the following values to use as the reservation principle for items that belong to the selected model group (including items that are on a BOM or formula line):
    - **Manual** - Items in this model group won't be physically reserved for production.
    - **Estimation** - Items in this model group will be physically reserved during the estimation phase of the production order.
    - **Scheduling** - Items in this model group will be physically reserved during the scheduling of the production order.
    - **Release** - Items in this model group will be physically reserved when production order is released.
    - **Start** - Items in this model group will be physically reserved at the start of the production order.

## Example of using reservation principles in a bulk/pack scenario

A bulk lubricant material is produced in a 1,000-liter mixer. Once the bulk material is ready, it is pumped out to several filling stations where the bulk lubricant is filled into bottles of different sizes. After filling, the bottles are packed into boxes, which are then packed onto pallets.

In this scenario, a batch order is created for making 1,000 liters of bulk material (this is the bulk order). When this batch order is completed, it is reported as finished to the material input location of the filling stations. A batch order for filling and packing each of the bottle sizes is created (these are the pack orders). The pack orders have a formula that consists of the bulk material, an empty bottle, a label, and other packing materials. Because the bulk material flows directly from the mixer tank into the filling station, no warehouse work is required to pick this ingredient and the bulk material is consumed directly from the input location. Therefore, the reservation principle is set to *manual*. The other materials are staged to the filling station by pick work and therefore the reservation principles for these lines are set, for example, to *release* so the reservation automatically happens when the pack order is released.
