---
title: Demand driven planning
description: The article describes how generate planned orders for items that are set up as decoupling points.
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

The article describes how generate planned orders for items that are set up as decoupling points. Here we have the same buffer levels we used in our example previously.

The trigger for a new planned order occurs when the net flow is below the reorder point level during the planning run. When you use DDMRP we expect that planning is run on a daily basis, so you are essentially checking your inventory levels once a day to determine whether it needs to be replenished. You can see on the bottom of the screen that we calculate net flow as being our on hand inventory plus inventory that is on order (which means existing supply orders that are not yet here) minus what we term to be qualified demand.

![Chart  funnel chart Description automatically generated](media/image16.png)

When the order is triggered, the amount of the order will be the maximum level minus the net flow, as indicated on the graphic. We also leverage the functionality that was added with priority based planning to assign an order priority instead of using requirement dates. In DDMRP we use the % of maximum inventory as the rule for assigning the priority of the planed order. In this case, our % of maximum is about 60% so the order priority for replenishment will be 60 (where 0 is the highest priority and 100 is the lowest)

Qualified demand is shown in more detail on the next picture.

![Chart Description automatically generated](media/image17.png)

Qualified demand = the demand past due plus today's demand, plus qualified order spikes in the future. If we look at the chart on the bottom left, we assume today is June 12 and we can see our demand for today and the next three days.

With DDMRP we can set an order spike threshold to identify demand that exceeds our normal expectations. If we set that threshold at 25 eaches then we would identify that two of our future dates qualify as order spikes.

So now, I can calculate qualified demand, assuming there is no demand past due. We will add today's demand of 18 plus the quantities of our two order spikes, 29 and 26 eaches and we get a qualified demand of 73. Notice that even though we have demand for June 15th we are not going to use it in our net flow calculation because DDMRP is different that our traditional planning coverage groups in the way we trigger planned orders.

## Generate planned orders with DDMRP

The first of all we review the net requirements.

We have 220 eachs of this item from our example above on hand.

We have an order for 18 today, an order for 29 tomorrow, 26 the following day and 20 on the 23rd. You can see here that we have a flag to say that these two orders have been identified as spikes.

![Graphical user interface Description automatically generated](media/image18.png)

Now let's select update and run master planning and see what happens. Remember, master planning will generate a planned order if the net flow drops below the reorder point, which in this example was 219 units.

![Graphical user interface Description automatically generated](media/image19.png)

Now we have our results – we got a planned purchase order for a quantity of 130, which is the maximum level minus our net flow. The planned order gets assigned a priority of 53.07 based on the % of maximum strategy.

> [!NOTE]
> The Planning optimization calculates only decoupled items as DDMRP. The rest of items are calculated as standard MRP.
