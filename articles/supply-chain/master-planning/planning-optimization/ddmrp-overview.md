---
title: Demand Driven Material Requirements Planning overview
description: Demand Driven Material Requirements Planning (DDMRP) is a planning methodology that is based on decoupling supply and demand by setting up decoupling-points items. For those items, buffers are maintained to ensure the right amount of stock is kept.
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

[!include [banner](../../includes/banner.md)]

For years, companies have used material requirements planning (MRP) as a system for calculating the materials and components needed to manufacture a product. However, supply chains have now changed. Parts are increasingly sourced from overseas and therefore have long lead times, so many companies have reported suffering stockouts or overstocks due to not knowing how much inventory to stock. There is also more market fluctuation (sometimes inaccurately forecast) and customers are demanding products with a short lead time, so there are supply chain shortages all over the world. And on top of that, MRP tools often give planners thousands of actions to do, so it's hard to know what to focus on. Often, the solution to many of these problems is to switch to Demand Driven Material Requirements Planning (DDMRP).

Demand Driven Material Requirements Planning (DDMRP) is a planning methodology that is based on decoupling supply and demand by setting up decoupling-points items. For those items, buffers are maintained to ensure the right amount of stock is kept. By decoupling supply and demand, the bullwhip effect is avoided because variability is not passed through the chain. The buffer is intended to cover the average usage of the part (pulling from the buffer) and can also be adjusted cover demand spikes.

DDMRP has proven to be a valuable planning methodology for variable environments where customer tolerance times are shorter than cumulative lead times.

## The five components of DDMRP

DDMRP has five sequential components. The first three components essentially define the initial and evolving configuration of a demand driven material requirements planning model. The final two elements define the day-to-day operation of the method. The 5 processes (steps) of DDMRP are:

- **[Strategic inventory positioning](ddmrp-inventory-positioning.md)** — Identify decoupling points in the supply chain network. These are specific points of your supply chain where you're going to place an inventory buffer that you will monitor and replenish.
- **[Buffer profiles and levels](ddmrp-buffer-profile-and-levels.md)** – For each decoupling point, identify the buffer sizes (minimum and maximum stock levels) and the reorder quantity.
- **[Dynamic buffer adjustments](ddmrp-dynamic-adjustments.md)** – Adjust buffer levels based on varying operating parameters or planned future events.
- **[Demand driven planning](ddmrp-planning.md)** — Generate supply orders as needed. This includes manufacturing orders, purchase orders, and stock transfer orders
- **[Highly collaborative and visible execution](ddmrp-visual-and-collaborative-execution.md)** — Execute the supply orders with the help of visualization.

DDMRP is typically used by manufacturers who have a multi-level bill of material, but you can also apply it to distribution and retail networks.

## DDMRP in Dynamics 365 Supply Chain Management

In Supply Chain Management, DDMRP functionality has been added to the existing Master planning module, but requires that you use the Planning Optimization Add-in. DDMRP is included with Supply Chain Management and requires no additional license fees.

DDMRP is integrated with the existing planning setups in Supply Chain Management and is used together with them to arrive at the right planning configuration for your business. It is controlled by a new coverage code that is completely different from period, min/max, requirement, and so on. It isn't a new module, and it does not replace existing planning functionality, but it does give you more functionality to use.
