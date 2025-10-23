---
title: Inventory marking
description: Learn about the options that are available for marking inventory in firmed orders, including outlines on marking and pegging.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
ms.topic: how-to
ms.date: 07/21/2025
ms.custom:
  - bap-template
---

# Inventory marking

[!include [banner](../../includes/banner.md)]

This article provides information about the options that are available for marking inventory in firmed orders.

*Marking* is used to link supply and demand. It resembles *pegging*, which indicates how master planning expects to cover demand. From a planning point of view, the main difference is that marking is more permanent than pegging.

Marking was introduced to support special costing scenarios for first in, first out (FIFO) and last in, first out (LIFO). However, it's now also used for some non-costing scenarios. Marking between supply and demand is optional and almost permanent. Marking can be removed manually by a user, or it can be removed by running a sales order line explosion where the **Remove marking** option is selected.

Pegging is controlled by master planning during coverage to link demand with the required supply. Pegging can be updated for each planning run to optimize the supply that is required to cover demand. When master planning updates pegging information, it respects any existing marking.

Pegging starts by including relevant marking, on-hand reservations, and on-order reservations, in the following sequence:

1. Marking between demand and supply
1. On-hand reservations
1. On-order reservations

When you firm a planned order, the **Firming** dialog box provides an **Update marking** field that you use to set marking options for the orders that are created during firming. Select one of the following values:

- *No* – No inventory marking is applied.
- *Standard* – Inventory marking is updated according to the pegging. A requirement order (demand) is marked against a fulfillment order (supply). If some quantity remains on the fulfillment order, it isn't marked, and the reference information is left blank. For example, if a sales order for 100 ea is pegged against a purchase order for 150 ea, reference information will be assigned only to the sales order.
- *Extended* – Both the requirement order (demand) and the fulfillment order (supply) are marked, regardless of any quantity that remains on the fulfillment order. For example, if a sales order for 100 ea is pegged against a purchase order for 150 ea, reference information will be assigned to both the sales order and the purchase order.
- *Single level standard* – Single-level marking is used. Single-level marking marks only the main item, not its bill of materials (BOM) components. Therefore, you can keep component assignment for production orders flexible after firming. Single-level marking enables the system to optimize for last-minute demand changes. In *standard* single-level marking, requirement orders are marked against their fulfillment orders, but fulfillment orders aren't marked if they have remaining quantity.
- *Single level extended* – Single-level marking is used. In *extended* single-level marking, requirement orders are marked against their fulfillment orders, and fulfillment orders are always marked, regardless of whether any quantity remains.

To set the default marking option for your system, go to **Master planning** \> **Setup** \> **Master planning parameters**. Then, on the **Standard update** tab, set the **Update marking** field to your preferred option.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
