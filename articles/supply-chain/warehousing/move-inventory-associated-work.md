---
# required metadata

title: Movement of inventory with associated work in Warehouse management
description: Using movement of inventory, you can decide which warehouse workers are allowed to move reserved inventory.
author: Mirzaab
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSWorker
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Movement of inventory with associated work in Warehouse management

[!include [banner](../includes/banner.md)]

Using movement of inventory, you can decide which warehouse workers are allowed to move reserved inventory. This provides a flexibility in regulated warehouses where you can decide to not allow a worker to choose a new pick location for pick work that is already created. It also allows a warehouse manager to control which capabilities some less experienced workers should have.

The flexibility to manage the daily operations of warehouse workers can be useful in scenarios such as these:

## Scenario 1

A company has a relatively small receiving area, and it’s congested with pallets and boxes awaiting put away. A large shipment is expected on the current day, so the receiving clerk decides to clear up the receiving area by moving some of the pallets to a secondary inbound staging area.

## Scenario 2

An experienced warehouse worker notices an opportunity in a warehouse to consolidate items in one location instead of having them divided across three nearby locations with little quantity on each. The worker wants to consolidate the quantity by moving items from each of these locations into the same location and onto the same license plate.

## Scenario 3

A pallet is awaiting shipment in a staging location, such as STAGE01, which is near BAYDOOR01. However, due to a change of plans the truck is scheduled to arrive at BAYDOOR04. The shipping clerk is aware of this and needs to ensure that the truck does not have to wait to be loaded from STAGE01. The shipping clerk decides to move the items in that shipment from STAGE01 to STAGE04, which is closer to the new destination.

### Current limitations

The work reservations that you can move are limited to Sales order, Transfer order issue, Transfer order receipt, Purchase order, and Replenishment work.

Moving items is restricted to prevent splitting of work lines. This means that if you have a work line for 100 pcs of item A from location Loc1, you won’t be able to move only 30 pcs of item A from there to another location. This would lead to a split of the existing work line to 30 and 70, because the locations are now different.

For staging scenarios, where the license plate you move the goods from or the license plate you move the goods to, are set as a Target LP for a work order, only movement of the entire LP is allowed, so as not to break up the Target LP.

Only the ad hoc movement is currently supported. That means that you will not be able to move reserved inventory through the movement by template mobile device menu items.

### Set up permission to move reserved inventory for individual workers

For the worker who is allowed to move reserved inventory, select the **Allow movement of inventory with work associated** check box under **Warehouse management \> Setup \> Worker**.  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
