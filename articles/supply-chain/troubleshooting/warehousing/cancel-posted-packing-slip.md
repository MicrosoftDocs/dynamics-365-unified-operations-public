---
title: Can't cancel packing slip after it's posted from an order
description: When picking and shipping processes are enabled for WMS, you can't cancel a packing slip after it's posted from a sales order. This page offers a workaround.
author: perlynne
ms.date: 06/24/2021
ms.topic: troubleshooting
# ms.search.form:
audience: Application User
ms.reviewer: kamaybac 
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-06-24
ms.dyn365.ops.version: 10.0.20
---

# Can't cancel a packing slip after it's posted from a sales order

## Symptoms

When picking and shipping processes are enabled for advanced warehouse management (WMS), you can't cancel a packing slip after it's posted from a sales order.

## Resolution

To correct posted packing slips for items that are enabled for WMS, the posting must occur from the load, not from the order. Microsoft has evaluated this issue and has determined that it's a feature limitation.  

In general, a sales order that has been picked and shipped through warehouse management processes can be packing slip-updated from the load or shipment and the sales order document itself. However, if you packing slip-update the sales order from the sales order document, packing slip reversal still can't be done from the load or sales order. Therefore, we recommend that you use the packing slip posting from the load. In this case, the reversal that must be done from the load will be enabled.
