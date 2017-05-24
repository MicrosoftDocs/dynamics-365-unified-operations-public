---
# required metadata

title: Movement of inventory with associated work in Warehouse management
description: This topic describes how you set up and apply piece picking confirmation from a mobile device.
author: BibiSp
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: bis
# ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Movement of inventory with associated work in Warehouse management

[!include[banner](../includes/banner.md)]

In Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, July 2017 update, you can decide, which warehouse workers are allowed to move reserved inventory, and which are not. This allows a flxibility in regulated warehouses where the preferred approach is to not accept that a worker can decide upon a new pick location from an already created pick work. It also allows a warehouse manager to control which capabilities some less experienced workers should have.

The flexibility in managing the daily operations of warehouse workers can be usefull in scenarios as these:

## Scenario 1
A company has a relatively small receiving area, and it’s congested with pallets and boxes awaiting put away. A large shipment is expected on the current day, so the receiving clerk decides to clear up the receiving area by moving some of the pallets to a secondary inbound staging area.

## Scenario 2
An experienced warehouse worker happens to notice an opportunity in a warehouse to consolidate items in one location instead of having them divided across 3 nearby locations with a little quantity in each. The worker would want to consolidate the quantity by moving items from each of these locations into the same location and onto the same license plate.

## Scenario 3
A pallet is awaiting shipment in a staging location, say, STAGE01, which is near BAYDOOR01. However due to a change of plans the truck is going to arrive to BAYDOOR04. The shipping clerk is aware of this and needs to ensure the truck does not have to hang around waiting to be loaded from STAGE01. The shipping clerk therefore decides to move the items in that shipment from STAGE01 to STAGE04, much closer to their new destination.

### Current limitations

The work reservations that are possible to move as of today are limited to Sales order, Transfer order issue, Transfer order receipt, Purchase order and Replenishment work.

Moving the items is restricted in a way that prevents splitting of work lines. So if you have a work line for 100 pcs of item A from location Loc1, you won’t be able to move only, say, 30 pcs of item A from there to another location, as that would lead to split of the existing work line to 30 and 70, as the locations are now different.

For Staging scenarios, where the license plate we move the goods from, or the license plate we move the goods to, are set as a Target LP for a work order, only movement of the entire LP is allowed, so as not to break up the Target LP.
Only the ad hoc movement is currently supported. That means you will not be able to move reserved inventory through the movement by template mobile device menu items.

Set up the permission to move reserved inventory for individual workers

For the worker that should be allowed to move reserved inventory, select the **Allow movement of inventory with work associated** check box under **Warehouse management** > **Setup** > **Worker**.  

### Backported

This feature has also been back-ported to Microsoft Dynamics AX 2012 R3 and will be available as part of CU12.
It can also be downloaded individually through KB number 3192548 

