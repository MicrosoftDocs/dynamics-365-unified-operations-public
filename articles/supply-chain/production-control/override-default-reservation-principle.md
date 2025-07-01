---
title: Override the default reservation principle for materials in production
description: Learn how to set a default reservation principle for each item model group, so that different reservation principles can automatically be applied.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventModelGroup
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Override the default reservation principle for materials in production

[!include [banner](../includes/banner.md)]

The *Override default production reservation* feature lets you set a default reservation principle for each item model group. Therefore, different reservation principles can automatically be applied for each item that is part of a production bill of materials (BOM) or batch order formula. You can select whether each item model group should override the default reservation principle that is set for an order, and what reservation principle should be used instead (*manual*, *estimation*, *scheduling*, *release*, or *start*).

When you create a new production order or batch order, the system prompts you to select the reservation principle for that order and all its BOM or formula lines. If you use the *Override default production reservation* feature, some or all BOM or formula lines can override your selected reservation principle and instead use the reservation principle set for their item model group.

For example, if you have raw materials or ingredients that require pick work, BOM or formula lines that are created for those products require a physical reservation, because physical reservation is a prerequisite for the generation of warehouse work. Typically, if you want the reservation to occur automatically, you select one of the following reservation principles: *estimation*, *scheduling*, *release*, or *start*. On the other hand, if you have materials or ingredients that don't require pick work, because they're consumed directly from a location, you typically select the *manual* reservation principle, which doesn't make any physical reservations or generate any pick work.

## Assign a production reservation policy to an item model group

1. Go to **Cost management \> Inventory accounting policies setup \> Item model groups**.
1. Create or select an item model group.
1. On the **Inventory policies** FastTab, select the **Override item production reservation** check box.
1. In the **Reservation** field, select the reservation principle for items that belong to the selected model group. (Those items include items that are on a BOM or formula line.)

    - *Manual* – Items in the model group aren't automatically physically reserved for production. However, they can still be manually reserved as required.
    - *Estimation* – Items in the model group are physically reserved during estimation of the production order.
    - *Scheduling* – Items in the model group are physically reserved during scheduling of the production order.
    - *Release* – Items in the model group are physically reserved when the production order is released.
    - *Start* – Items in the model group are physically reserved at the start of the production order.

## Example: Using reservation principles in a bulk/pack scenario

A bulk lubricant material is produced in a 1,000-liter mixer. After the bulk material is ready, it's pumped out to several filling stations, where bottles of different sizes are filled. After filling is completed, the bottles are packed into boxes. Those boxes are then packed onto pallets.

In this scenario, a batch order to make 1,000 liters of bulk material is created. (This order is the bulk order.) When this batch order is completed, it's reported as finished to the material input location of the filling stations. A batch order to fill and pack each bottle size is then created. (These orders are the pack orders.) The pack orders have a formula that consists of the bulk material, an empty bottle, a label, and other packing materials. Because the bulk material flows directly from the mixer tank to the filling stations, no warehouse work is required to pick this ingredient, and the bulk material is consumed directly from the input location. Therefore, the reservation principle is set to *manual*. The other materials are staged to the filling station by pick work. Therefore, the reservation principle for these lines is set to *release*, for example, so that the reservation automatically occurs when the pack order is released.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
