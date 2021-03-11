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

This feature is used when running [Cloud and edge scale units for manufacturing and warehouse management workloads](cloud-edge-workload-warehousing.md).

When a scale unit warehouse management workload does an inbound or outbound warehouse app inventory on-hand adjustment, the physical on-hand update will get processed via a **Warehouse management > Periodic tasks > Warehouse inventory adjustment journal**.

The following warehouse app work processes are currently using the **Warehouse inventory adjustment journal** on the scale unit workloads:
-	Adjustment in/out
-	Cycle counting
-	License plate loading

Several inventory transactions will get created as part of a cloud & edge inventory adjustment process because the two deployments ‘share’ the inventory. Let’s look at an example of adding on-hand.

## Inventory adjustment example

First the scale unit workload will create a Warehouse inventory adjustment transaction for the positive physical adjustment which will get synchronized to the hub and thereby result in increase of the on-hand on the hub.

| Type                                    | Scale unit | Direction | Hub |
|-----------------------------------------|------------|-----------|-----|
| Warehouse inventory adjustment          | +1         | ->        | +1  |


The hub will now process a counting journal posting via the  [Message processor messages](cloud-edge-message-processor-messages.md) to get the cost updated for the additional inventory on-hand and to not get double inventory on-hand the hub will create an offset transaction as part of this process and thereby remove the previously recorded on-hand related to the Warehouse inventory adjustment.

| Type                                    | Scale unit | Direction | Hub |
|-----------------------------------------|------------|-----------|-----|
| Counting                                | +1         | <-        | +1  |
| Warehouse inventory adjustment (Offset) | -1         | <-        | -1  |

You can on the hub from the first **Warehouse inventory adjustment journal** inquire and jump to both the *Counting journal* and the *Offset warehouse inventory adjustment journal* which was created as part of the adjustment process.
