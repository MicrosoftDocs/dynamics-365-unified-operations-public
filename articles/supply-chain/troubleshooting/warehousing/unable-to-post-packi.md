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
<!-- KFM: ms.search.form only mentions WHSLoadTable. Might this also occur from the sales order itself? -->
# Can't post packing slip for a stopped a sales order line

Error code: SYS13203

## Symptoms

The system displays the followign error message:

> Unable to post packing slip when stopping a sales order line after confirming the outbound shipment

The system displays the following error message:

> A quantity cannot be picked.

<!-- KFM: Which is the right error message, the first one, second one, or either/both of them? Can we tell something more, like where the user was and what the user was trying to do when this message appeared? -->

## Cause

One or more of the relevant sales order lines may be stopped, which means that the system will prevent further processing of that sales order. Among other things, this means that the system won't post a packing slip for the order.

If the outbound shipment has already been confirmed, that means that the shipment containing the sales order has already physically left the warehouse, so it's no longer possible to physically stop shipment of the sales order. <!-- KFM: Why are we mentioning this? Is this situation related to this error somehow? -->

## Resolution

To be able to post the packing slip, make sure that none of the relevant sales order lines are stopped by doing the following steps. <!-- KFM: I thought this should be more explicit. Please confirm this procedure. -->

1. Go to **All sales orders \> Sales and marketing \> All sales orders**.
1. Find and open the sales order that you are having trouble with.
1. On the **Sales order lines** FastTab, select a sales order line.
1. On the **Line details** FastTab, open the **General** tab and make sure the **Stopped** field is set to *No*.
1. Continue working until all of the relevant sales lines are no longer stopped. <!-- KFM: Is this step needed? (I.e., do we post packing slips for the entire order, or for one line at a time?) -->
1. Try again to post the packing slip for the order. <!-- KFM: Or order line or load? Where are we when we do this? -->
