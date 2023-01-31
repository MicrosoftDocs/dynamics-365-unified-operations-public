---
title: Demand Driven Material Requirements Planning (DDMRP) overview
description: This article provides information about Demand Driven Material Requirements Planning (DDMRP), a planning methodology that is based on the decoupling of supply and demand.
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

# Demand Driven Material Requirements Planning (DDMRP) overview

[!include [banner](../../includes/banner.md)]

For years, companies have used material requirements planning (MRP) as a system for calculating the materials and components that are required to manufacture a product. However, supply chains have now changed. Parts have longer lead times because they are increasingly sourced from overseas. Therefore, many companies have reported experiencing stockouts or overstocks, because they don't know how much inventory to stock. There is also more market fluctuation (sometimes inaccurately forecast), and customers are demanding products at a short lead time. Therefore, there are supply chain shortages all over the world. In addition, MRP tools often give planners thousands of actions to do. Therefore, it's hard to know what to focus on. Often, the solution to many of these issues is to switch to Demand Driven Material Requirements Planning (DDMRP).

DDMRP is a planning methodology that is based on the decoupling of supply and demand. This decoupling is achieved by setting up decoupling point items. For those items, buffers are maintained to ensure that the correct amount of stock is kept. The decoupling of supply and demand helps prevent the "bullwhip effect," because variability isn't passed through the chain. (The *bullwhip effect* refers to how small fluctuations in demand at the retail level can cause progressively larger fluctuations in demand at the wholesale, distributor, manufacturer, and raw material supplier levels.) Each buffer is intended to cover the average use of a part and can also be adjusted to cover demand spikes.

DDMRP has been proven to be a valuable planning methodology for variable environments where customer tolerance times are shorter than cumulative lead times.

## The five components of DDMRP

DDMRP has five sequential components (steps). The first three components essentially define the initial and evolving configuration of a demand-driven material requirements planning model. The last two components define the day-to-day operation of the methodology.

1. **[Strategic inventory positioning](ddmrp-inventory-positioning.md)** – Identify decoupling points in the supply chain network. Decoupling points are specific points of your supply chain where you put an inventory buffer that you will monitor and replenish.
2. **[Buffer profiles and levels](ddmrp-buffer-profile-and-levels.md)** – For each decoupling point, identify the buffer sizes (minimum quantity, maximum quantity, and reorder point) and the reorder quantity.
3. **[Dynamic buffer adjustments](ddmrp-buffer-profile-and-levels.md#dynamic-adjustments)** – Adjust buffer levels, based on varying operating parameters or planned future events.
4. **[Demand-driven planning](ddmrp-planning.md)** – Generate supply orders as they are required. These supply orders include manufacturing orders, purchase orders, and stock transfer orders
5. **[Highly collaborative and visible execution](ddmrp-visual-and-collaborative-execution.md)** – Run the supply orders with the help of visualization.

DDMRP is typically used by manufacturers that have a multi-level bill of materials (BOM). However, it can also be applied to distribution and retail networks.

## DDMRP in Dynamics 365 Supply Chain Management

DDMRP is included with Microsoft Dynamics 365 Supply Chain Management and requires no additional license fees. In Supply Chain Management, DDMRP functionality has been added to the existing **Master planning** module. However, it requires that you use the Planning Optimization Add-in.

DDMRP is integrated with the existing planning setups in Supply Chain Management and is used together with those setups to arrive at the correct planning configuration for your business. It's controlled by a new coverage code that is completely different from period, min/max, requirement, and so on. It isn't a new module, and it doesn't replace existing planning functionality. However, it does give you more functionality to use.
