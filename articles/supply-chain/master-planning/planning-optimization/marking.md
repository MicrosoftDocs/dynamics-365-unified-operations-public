---
# required metadata

title: Marking firmed orders with Planning Optimization
description: This topic provides information about the options available for marking firmed orders when you are using Planning Optimization. 
author: ChristianRytt
manager: tfehr
ms.date: 12/02/2020
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
ms.search.validFrom: 2020-12-02
ms.dyn365.ops.version: AX 10.0.13

---
# Marking firmed orders with Planning Optimization

[!include [banner](../../includes/banner.md)]

This topic provides information about the options available for marking firmed orders when you are using Planning Optimization.

Marking links supply and demand, like pegging that indicates how master planning expects to cover demand. From a planning point of view, the main difference is that marking is more permanent than pegging.

*Marking* was introduced to support special costing scenarios for first in first out (FIFO) and last in first out (LIFO), but it is now also used for some non-costing scenarios. Marking between supply and demand is optional and almost permanent. Marking can be removed manually by a user or by running a sales order line explosion with the **Remove marking** option selected.

*Pegging* is controlled by master planning during coverage to link demand with the required supply. Pegging can be updated for each planning run to optimize the supply needed to cover demand. When master planning updates pegging information, it respects any existing marking.

Pegging starts by including relevant marking, on-hand reservations, and on-order reservations in the following sequence:

1. Marking between demand and supply
1. On-hand reservations
1. On-order reservations

When you firm a planned order, the **Firming** dialog box provides an **Update marking** setting, which sets marking options for the orders created during firming. Choose one of the following options:

- **No** – No inventory marking is applied.
- **Standard** – Inventory marking is updated according to the pegging. A requirement order (demand) is marked against a fulfillment order (supply). If some quantity remains on the fulfillment order, it is not marked, and the reference information is left blank. For example, if a sales order for 100 ea is pegged against a purchase order for 150 ea, only the sales order will be assigned reference information.
- **Extended** – Both the requirement order (demand) and the fulfillment order (supply) are marked, regardless of whether any quantity remains on the fulfillment order. For example, if a sales order for 100 ea is pegged against a purchase order for 150 ea, both the sales order and the purchase order will be assigned reference information.
