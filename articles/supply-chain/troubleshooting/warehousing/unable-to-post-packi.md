---
title: Can't post packing slip for a stopped a sales order line
description: You are unable to post packing slip for a stopped a sales order line
author: smithanataraj
ms.date: 03/07/2022
ms.topic: article
ms.search.form: WHSLoadTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mfp
ms.search.validFrom: 2022-03-07
ms.dyn365.ops.version: 10.0.26
---

# Can't post packing slip for a stopped a sales order line

Error code: SYS13203

## Symptoms

When you are trying to post a packing slip for a load, the system displays the following error message:

> Unable to post packing slip when stopping a sales order line after confirming the outbound shipment
> A quantity cannot be picked.

## Cause

One or more of the related sales order lines may be stopped, which means that the system will prevent further processing of that sales order. Among other things, this means that the system won't post a packing slip for the order.

For example, a user may have decided to stop one or more order lines because the customer called back and canceled their order. However, if the outbound shipment had already been confirmed, then the shipment containing the sales order would have already physically left the warehouse, which means that stopping the sales order lines won't have any effect. Because it's no longer possible to physically stop the shipment, you may as well unstop lines so you can post the packing slip. You will then need to handle the canceled order as a return.

## Resolution

To be able to post the packing slip, make sure that none of the relevant sales order lines are stopped by doing the following steps.

1. Go to **All sales orders \> Sales and marketing \> All sales orders**.
1. Find and open the sales order that you are having trouble with.
1. On the **Sales order lines** FastTab, select a sales order line.
1. On the **Line details** FastTab, open the **General** tab and make sure the **Stopped** field is set to *No*.
1. Continue working until all of the relevant sales lines are no longer stopped.
1. Try again to post the packing slip for the load or sales order.
