---
# required metadata

title: Message processor messages for cloud and edge workloads
description: This topic provides information about the Warehouse inventory adjustment journal and processing.
author: perlynne
manager: tfeyr
ms.date: 03/10/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSInventoryAdjustmentJournal, InventJournalCount   
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: perlynne
ms.search.validFrom: 2021-04-21
ms.dyn365.ops.version: 10.0.19
---

# Warehouse inventory adjustment

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This feature is used when running cloud and edge scale units for [manufacturing workloads](cloud-edge-workload-manufacturing.md) and [warehouse management workloads](cloud-edge-workload-warehousing.md).

When a worker does an inventory adjustment using the warehouse app against a scale unit warehouse management workload, the physical on-hand update must get processed using the **Warehouse inventory adjustment journal** page (**Warehouse management > Periodic tasks > Warehouse inventory adjustment journal**).

The following warehouse app work processes currently use the **Warehouse inventory adjustment journal** on scale unit workloads:

- Adjustment in/out
- Cycle counting
- License plate loading

Several inventory transactions are created as part of a cloud and edge inventory adjustment process because the two deployments share the inventory. Let's look at an example of adding on-hand.

## Inventory adjustment example

First, the scale unit workload creates a warehouse inventory adjustment transaction for the positive physical adjustment, which will be synchronized to the hub and thereby result in an increase of the on-hand on the hub.

| Type                                    | Scale unit | Direction | Hub |
|-----------------------------------------|------------|-----------|-----|
| Warehouse inventory adjustment          | +1         | ->        | +1  |

The hub now processes a counting journal posting via the  [Message processor messages](cloud-edge-message-processor-messages.md) update the additional inventory on-hand. To prevent double inventory on-hand, the hub creates an offset transaction as part of this process and thereby removes the previously recorded on-hand related to the warehouse inventory adjustment.

| Type                                    | Scale unit | Direction | Hub |
|-----------------------------------------|------------|-----------|-----|
| Counting                                | +1         | <-        | +1  |
| Warehouse inventory adjustment (Offset) | -1         | <-        | -1  |

Once a scale unit has created a *Warehouse inventory adjustment journal* on the hub, you can review both the *Counting journal* and the *Offset journal*, which are created by the hub as part of the adjustment process.
