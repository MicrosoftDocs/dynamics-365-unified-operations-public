---
# required metadata

title: Marking with Planning Optimization
description: This topic explains how to start to use the Planning Optimization functionality. 
author: ChristianRytt
manager: tfehr
ms.date: 11/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-11-18
ms.dyn365.ops.version: AX 10.0.13

---
# Marking set when firming planned orders

[!include [banner](../../includes/banner.md)]

This topic provides information about marking, related to the options available when firming a planned order. 

Marking link supply and demand, like pegging that indicates how master planning expect to cover demand. From a planning point of view, the main difference is that marking is more permanent than pegging.

**Marking** was introduced to support special costing scenarios for FIFO and LIFO but is now also used for some non-costing scenarios. Marking between supply and demand is optional and almost permanent. Marking can be removed manually by user or by running sales order line explosion with Remove marking check marked.

**Pegging** is controlled by master planning during coverage to link demand with the required supply. Pegging can be updated for each planning run to optimize the supply needed to cover demand. When master planning update pegging information it respects any existing marking.

Pegging starts by including relevant marking, on-hand reservations, and on-order reservations in the following order sequence:

1. Marking between demand and supply
2. On hand reservations
3. Order reservations

When firming planned orders, you have 3 marking options for the orders created during firming.

- **No**  – No inventory marking is performed.
- **Standard**  – Inventory marking is updated according to the pegging. A requirement order (demand) is marked against a fulfillment order (supply). If some quantity remains on the fulfillment order, it is not marked, and the reference information is left blank.
Example: If a sales order for 100 ea is pegged against a purchase order for 150 ea, only the sales order will get reference information.

- **Extended**  – Both the requirement order (demand) and the fulfillment order (supply) are marked, regardless of whether any quantity remains on the fulfillment order.
Example: If a sales order for 100 ea is pegged against a purchase order for 150 ea, both the sales order and the purchase order will get reference information.
