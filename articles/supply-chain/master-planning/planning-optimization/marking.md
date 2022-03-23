---
# required metadata

title: Inventory marking with Planning Optimization
description: This topic provides information about the options that are available for marking inventory in firmed orders when you use Planning Optimization.
author: t-benebo
ms.date: 12/02/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2020-12-02
ms.dyn365.ops.version: AX 10.0.13

---
# Inventory marking with Planning Optimization

[!include [banner](../../includes/banner.md)]

This topic provides information about the options that are available for marking inventory in firmed orders when you use Planning Optimization.

*Marking* is used to link supply and demand. It resembles *pegging*, which indicates how master planning expects to cover demand. From a planning point of view, the main difference is that marking is more permanent than pegging.

Marking was introduced to support special costing scenarios for first in, first out (FIFO) and last in, first out (LIFO). However, it's now also used for some non-costing scenarios. Marking between supply and demand is optional and almost permanent. Marking can be removed manually by a user, or it can be removed by running a sales order line explosion where the **Remove marking** option is selected.

Pegging is controlled by master planning during coverage to link demand with the required supply. Pegging can be updated for each planning run to optimize the supply that is required to cover demand. When master planning updates pegging information, it respects any existing marking.

Pegging starts by including relevant marking, on-hand reservations, and on-order reservations, in the following sequence:

1. Marking between demand and supply
1. On-hand reservations
1. On-order reservations

When you firm a planned order, the **Firming** dialog box provides an **Update marking** field that you use to set marking options for the orders that are created during firming. Select one of the following values:

- **No** – No inventory marking is applied.
- **Standard** – Inventory marking is updated according to the pegging. A requirement order (demand) is marked against a fulfillment order (supply). If some quantity remains on the fulfillment order, it isn't marked, and the reference information is left blank. For example, if a sales order for 100 ea is pegged against a purchase order for 150 ea, reference information will be assigned only to the sales order.
- **Extended** – Both the requirement order (demand) and the fulfillment order (supply) are marked, regardless of any quantity that remains on the fulfillment order. For example, if a sales order for 100 ea is pegged against a purchase order for 150 ea, reference information will be assigned to both the sales order and the purchase order.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]