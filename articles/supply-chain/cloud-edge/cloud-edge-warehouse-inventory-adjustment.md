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

When a worker does an inventory adjustment using the warehouse app against a scale unit warehouse management workload, the physical on-hand update must be processed by the *Warehouse inventory adjustment journal* batch job, which you run and schedule by going to **Warehouse management > Periodic tasks > Warehouse inventory adjustment journal**.

The following warehouse app work processes currently use the *Warehouse inventory adjustment journal* on scale unit workloads:

- Adjustment in/out
- Cycle counting
- License plate loading

Several inventory transactions are created as part of cloud and edge an inventory adjustment process because the hub and scale unit deployments share the inventory records.

## Inventory adjustment example

In this example, a warehouse worker has used the warehouse app to register the adding of on-hand inventory.

First, the scale unit workload creates a warehouse inventory adjustment transaction for the positive physical adjustment, which is then synchronized to the hub and thereby result in an increase of the on-hand on the hub.

| Type                                    | Scale unit | Direction | Hub |
|-----------------------------------------|------------|-----------|-----|
| Warehouse inventory adjustment          | +1         | ->        | +1  |

The hub then processes a counting journal posting, which are received through [message processor messages](cloud-edge-message-processor-messages.md), to update the additional inventory on-hand. To prevent double inventory on-hand, the hub creates an offset transaction as part of this process and thereby removes the previously recorded on-hand related to the warehouse inventory adjustment.

| Type                                    | Scale unit | Direction | Hub |
|-----------------------------------------|------------|-----------|-----|
| Counting                                | +1         | <-        | +1  |
| Warehouse inventory adjustment (Offset) | -1         | <-        | -1  |

Once a scale unit has created a *Warehouse inventory adjustment journal* on the hub, you can review both the *Counting journal* and the *Offset journal*, which are created by the hub as part of the adjustment process.

You can review each of these journal entires and transaction in Supply Chain Management by doing the following steps:
<!-- KFM: Please review and confirm this. -->

1. Sign in on the scale unit.
1. Go to <!-- KFM: Path? -->.
1. On the **Warehouse inventory adjustment journal** page, find and open the journal that recorded the on-hand inventory change. The **Journal lines** section shows each adjustment recorded by this journal.
1. Sign in on the hub.
1. Go to <!-- KFM: Path? -->.
1. On the **Warehouse inventory adjustment journal** page, you should see the same journal listed (provided the hub and scale unit have synced).
1. Open the journal. Provided the [message processor messages](cloud-edge-message-processor-messages.md) have been processed, you will see links to the **Counting journal** and the **Offset journal** in the header.
    - The **Counting journal** should show the same journal line that you saw on the scale unit.
    - The **Offset journal** should show the offset, which removes the double inventory adjustment.
    > [!NOTE]
    > When all syncing and processing is complete, the *Counting journal* and the *Offset journal* are synced back to the scale unit and can also be viewed from the relevant **Warehouse inventory adjustment journal** page there.
