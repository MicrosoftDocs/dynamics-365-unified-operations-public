---
title: Demand driven planning
description: The article describes how to generate planned orders for items that are set up as decoupling points.
author: t-benebo
ms.date: 06/30/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-06-30
ms.dyn365.ops.version: 10.0.28
---

# Demand driven planning

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

The article describes how to generate planned orders for items that are set up as decoupling points.

## Net flow and qualified demand

<!-- KFM: We should add some sub-headings for the theory. We should introduce the terms "net flow" and "qualified demand" and explain why we are talking about them here.  -->

The following illustration shows how net flow is calculated as on-hand inventory plus inventory that is on order (existing supply orders that aren't yet received) minus what we term to be qualified demand.
<!-- KFM: The figure also confuses me--what values are we showing here? -->

![Example net flow calculation chart.](media/ddmrp-net-flow-example.png "Example net flow calculation chart")

When a planned order is triggered during a planning run, the quantity ordered will be the maximum level minus the net flow. The system also leverages priority-based planning functionality to assign an order priority instead of using requirement dates. DDMRP uses the order quantity as a percentage of maximum inventory as the basis for assigning the priority of a planed order. In the previous illustration, the ordered quantity is 53% of the maximum quantity, so the order priority for replenishment will be 60 (where 0 is the highest priority and 100 is the lowest). <!-- KFM: this example doesn't fully make sense to me. Please confirm that we are still using the correct terms here. -->

*Qualified demand* is the demand past due plus today's demand, plus qualified order spikes in the future. The following illustration shows an example of demand levels for today (June 12) and the next three days. DDMRP lets you set an order spike threshold to identify demand that exceeds normal expectations. If the threshold is set at 25 pieces, then two of the future dates shown in the illustration would qualify as order spikes. <!-- We should explain how to set the threshold for each item (maybe with link to [Inventory positioning](ddmrp-inventory-positioning.md), provided we also document the setting there, which we don't right now.) -->

![Example qualified demand calculation chart.](media/ddmrp-net-qualified-demand-example.png "Example qualified demand calculation chart")

Assuming there's no demand past due, you can now add today's demand (18) to the quantities of the two order spikes (29 and 26), to get a qualified demand of 73. Notice that even though there's demand for June 15, this isn't included in the net flow calculation because DDMRP is different from traditional planning coverage groups in the way it triggers planned orders.

## Generating planned orders with DDMRP

During a planning run, the system will create a new planned order when the net flow for an item falls below the reorder point level. When you use DDMRP, you'll usually do a planning is run every day, so you're essentially checking your inventory levels once a day to determine which items need to be replenished.

The following screenshot shows <!-- What is this? Planned orders? What is the page name? --> an example of a situation where you have an order for 18 pieces on June 20, an order for 29 the next day, 26 the following day, and 20 on June 23. The spike threshold is set at 25 pieces, so two fo these orders are flagged as spikes. Finally, there are 220 pieces of this item on hand. <!-- These dates don't match those of the earlier bar graph. Are they supposed to? -->

![Planning example 1.](media/ddmrp-planning-example-1.png "Planning example 1")

Now let's select update <!-- Where do we select this? --> and run master planning and see what happens. Master planning will generate a planned order if the net flow drops below the reorder point, which in this example is 219 pieces. <!-- I don't understand this example. How does this math work? Why are we ordering on the 27th? -->

![Planning example 2.](media/ddmrp-planning-example-2.png "Planning example 2")

This example results in a planned purchase order for a quantity of 130, which is the maximum level minus the net flow. The planned order is assigned a priority of 53.07 based on its percentage of the maximum quantity.

> [!NOTE]
> Planning Optimization only calculates decoupled items using DDMRP. All other items are calculated using standard MRP.
