---
title: Demand Driven Material Requirements Planning overview
description: Demand Driven Material Requirements Planning (DDMRP) is a planning methodology that is based on decoupling supply and demand by setting decoupling-points items. For those items, buffers are maintained to ensure the right amount of stock is kept.
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

# Demand Driven Material Requirements Planning overview

[!include [banner](../includes/banner.md)]

So far, companies have been using MRP, but in the last years supply chains have changed- there are many parts that come from overseas, having long lead times and many companies reported suffering stockouts or overstocks, not knowing how much to stock.

There is higher market fluctuation, with more variability (sometimes not accurate forecast) and customer demanding products with a short lead time so, there are supply chain shortages all over the world.

And on top of that, MRP tools many times tell you as a planner thousands of actions to do, so you do not know what to focus on.

Current state MRP:

- Long lead times
- Stockouts and overstocks
- High market fluctuation
- Supply chain shortages
- MRP tools are confusing

In this context, it's where DDMRP appears.

Demand Driven Material Requirements Planning (DDMRP) is a planning methodology that is based on decoupling supply and demand through some decoupling points, items for which stock buffers will be maintained. By decoupling supply and demand, the bullwhip effect is avoided, as variability is not passed through the chain. For those items, buffers are maintained to ensure the right amount of stock is kept. The buffer is thought to cover the average usage of the part (pulling from the buffer) and it will also be replenished to cover for spikes.

It has proven to be a valuable planning methodology for variable environments where customer tolerance times are shorter than cumulative lead times.

In this topic it will be described how DDMRP is implemented in Dynamics 365 Supply Chain Management.

Demand Driven Material Requirements Planning has five sequential components. The first three components essentially define the initial and evolving configuration of a demand driven material requirements planning model. The final two elements define the day-to-day operation of the method.

The 5 processes (steps) of DDMRP are:

- **Strategic inventory positioning:** Setting or determining the decoupling points in the supply chain network.
- **Buffer profiles and levels:** Which is determining what are the minimum and maximum stock levels that should be kept for each decoupling point, as which as at which order quantity it should be reordered.
- **Dynamic buffer adjustments: Which is adjusting buffer levels based on varying operating** parameters or planned future events.
- **Demand driven planning:** This is the process where the supply orders will be generated. It includes manufacturing orders, purchase orders and stock transfer orders
- **Highly collaborative and visible execution**: execution on the supply orders. Visualization is provided to support the execution process.

Otherwise, DDMRP is a formal planning and execution method to protect and promote flow through the establishment of strategically placed decoupling point buffers. That means, in some specific points of your supply chain you're going to place an inventory buffer that you will replenish and monitor. And it has proven to help in all problems that are typical of classic MRP.

And what it really means with promoting and protecting flow is in different parts of your supply chain having a bill of material with different components. You would specify specific points and thanks to it we have those protected Strategic items they are called decoupling points.

Then the whole chain of having shorter lead times towards the customers, a whole service levels higher and that's why it is basically based itself and placing these strategically items that they're going to be decoupled and then you place buffers. You basically want to stock those items. And it will have a way of how much should you stock for those items. That is high level what DDMRP is about.

Placing stock in some specific points of your supply chain so the whole process of reaching to your customers better.

When we talk about what types of ways you can use DDMRP, we often think of examples that are relevant to manufacturers who have a multi-level bill of materials, but that is not the only application of DDMRP principles. You can also apply this theory and functionality to support distribution and retail networks, and we will make sure to highlight these use cases especially in the future sessions we have planned.

## DDMRP in Supply Chain Management

In Supply Chain Management, DDMRP functionality has been added to the existing Master Planning module, but requires that you use the Planning Optimization Add-in. DDMRP is included with Supply Chain Management and requires no additional license fees.

It is integrated with the existing planning setups and would be used together with the original planning setups to arrive at the right planning configuration for your business.

Ultimately this functionality is controlled by a new coverage code in Dynamics – it is completely different from period, min/max, requirement etc. In summary, it is not a new module, and it does not replace what we currently have but it gives you more functionality to use.

However, the DDMRP functionality is only compatible with the Planning Optimization service and does not work with classic Master Planning.

And finally, the functionality is included in the base licensing for Dynamics SCM and does not require any additional cost to use.

Now, the different steps of DDMRP and how to implement them in dynamics will be explained.

## Turn on DDMRP for your system

To enable this functionality the user needs to enable the features on feature management: priority-based planning and DDMRP for planning optimization

