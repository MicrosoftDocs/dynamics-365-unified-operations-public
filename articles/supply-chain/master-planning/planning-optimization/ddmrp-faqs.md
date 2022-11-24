---
title: DDMRP FAQ
description: This topic provides answers to frequently asked questions (FAQs) about Demand Driven Material Requirements Planning (DDMRP) in Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: faq
ms.date: 11/24/2022
ms.custom: bap-template
---

# DDMRP FAQ

This topic provides answers to frequently asked questions (FAQs) about Demand Driven Material Requirements Planning (DDMRP) in Dynamics 365 Supply Chain Management.

## General

### Q: Does DDMRP require Planning Optimization?

Yes, DDMRP functionality requires the Planning Optimization Add-in for Dynamics 365 Supply Chain Management and is not available for the [deprecated master planning engine](../deprecated-master-planning-overview.md). For more information about Planning Optimization, see [Get started with master planning](get-started.md)

### Q: Can priority-based planning be used together with DDMRP?

DDMRP uses priority-based planning functionality to set the priority of planned orders. It calculates the priority of each order by divining the net flow by the maximum inventory level. Master planning then uses the order priority (rather than the requirement date) to drive supply allocation.

### Q: I see this as an extension of the "min/max coverage code functionality. Do you see any scenarios where you would still use min/max functionality instead of DDMRP when producing or procuring stock?

One of the key differences between min/max and DDMRP is that DDMRP does not consider all future net requirements when determining whether to reorder. DDMRP is run daily and looks only at past-due demand (today's demand) and order spikes to determine whether an order needs to be placed immediately. Min/max looks at all demand in the coverage time fence and will propose planned orders further in the future based on when net requirements will deplete inventory below the minimum point.

### Q: Can you run the existing material requirements planning (MRP) functionality together with DDMRP, for example when using coverage groups?

Yes, we expect companies to run some combination of decoupling points with other coverage methods (such as min/max, period, or requirement). Decoupling points should be placed at strategic points in the supply chain but are not likely the right answer for every product, so it's likely that companies will run DDMRP along with other coverage types.

### Q: Can we simulate DDMRP using the past two years of data within Supply Chain Management?

Unfortunately not. You can easily create an excel sheet with the formulas and use that to check what the system would have created as the buffer values.

### Q: Is Supply Chain Management able to analyze whether an item is in the right coverage group (for example, to test whether the factors I set up for variability and so on will still meet my item consumption)?

No automated functionality currently exists for this in Supply Chain Management, but you can manually review the performance of your net flow and on-hand inventory. You can do so by checking the buffer values graph to see whether your actual net flow and on-hand inventory values are in the zones where you expect them to be.

### Q: Is there a data entity for importing usage history from legacy ERP systems?

Yes, a data entity exists for updating your past buffer value history if you come from another system and would like to keep that history.

### Q: Does DDMRP work with Supply Chain Management process manufacturing?

Yes, DDMRP works with any functionality that the deprecated master planning engine works with, provided you are using Planning Optimization.

### Q: Can DDMRP work with projects?

Yes, DDMRP works with any functionality that the deprecated master planning engine works with, provided you are using Planning Optimization.

### Q: Will DDMRP work in an intercompany scenario?

Yes, DDMRP works with any functionality that the deprecated master planning engine works with, provided you are using Planning Optimization.

## The Demand Driven Institute

### Q: Is Demand Driven Institute part of Microsoft?

No, the Demand Driven Institute is a separate organization, which developed the DDMRP methodology. Microsoft developed the functionality to support DDMRP methodology in Supply Chain Management and our solution has been certified by the Demand Driven Institute. For more information, see the [Demand Driven institute web site](https://www.demanddriveninstitute.com/).

### Q: Which Demand Driven Institute certifications are recommended for consulting teams?

The recommended certification is Demand Driven Planner (DDP). This certification includes all the DDMRP material and provides a deep understanding of DDMRP principles so consultants can be successful in explaining and implementing DDRMP in Supply Chain Management.

## Decoupling points

### Q: How can we decide where to define decoupling points?

When choosing where to place decoupling points in your supply chain, consider the following:

- **External variability** – Add buffers to mitigate the effects that could arise from supply variability that is out of your control.
- **Inventory leverage and flexibility** – Add buffers to prioritize items that are used as components in multiple products.
- **Critical operation protection** – Add buffers before critical operations or bottlenecks to ensure that operations don't sit idle due to a lack of raw materials.
- **Customer tolerance time** – Add buffers at stages where customers expect a short lead time for the item.
- **Sales order visibility horizon** – Add buffers at points where you need to react quickly to meet new demand.
- **Market potential lead time** – Add buffers at points where you can sell items at a higher price if the lead time is shorter.

For more information, see [Inventory positioning](ddmrp-inventory-positioning.md).

### Q: Are negative and positive days taken into consideration for coverage code decoupling points?

No, negative and positive days are not considered by the DDMRP model.

### Q: Decoupling points can only be added at the item coverage level. Should we continue to indicate the coverage group at the item level so it can be considered for other locations not specified in the item coverage?

Yes, it is possible that not all locations for a given item need to be set up as decoupling points, so you can choose to have a coverage group for an item that uses min/max, period, requirement, and so on, and then identify the specific decoupling points on the item coverage page, which will override the item-level coverage group.

### Q: Is the new coverage code compatible with all product and storage dimensions?

Yes, the "decoupling point" coverage code works with all products and storage dimensions. You must specify all the dimensions for a product that is a decoupling point.

### Q: Is it necessary to create item coverage records for every variant of a product or can the calculation be run on product masters?

Decoupling points must be set on the product variant level because each variant will have its own demand pattern and planned orders are generated on the variant level.

## Planned order generation with DDMRP

### Q: Does DDMRP plan based on forecast values unless qualified demand (orders) for the time frame is greater than forecast?

DDMRP does not use forecasts to generate planned orders. Planned orders are created when the net flow is below the reorder point.

Forecasts are used when the system is set to calculate average daily usage (ADU) based on a *Forward* or *Blended* time period. ADU is one of the factors that affect the buffer values (minimum, reorder point, and maximum) so it indirectly affects how much you would reorder.

### Q: How is production scheduling done when a manufactured part uses DDMRP?

Planned production orders are generated and assigned a priority value based on the net flow divided by the maximum inventory level. Master planning then uses that order priority (instead of the requirement date) to schedule production instead.

### Q: If I set up a maximum reorder quantity that is lower than the reorder quantity, will DDMRP generate multiple planned orders with different priority values?

The default order settings are respected when planned orders are created, and all planned orders will be assigned the same priority.

If you need different priorities to be assigned to different parts, then use planning priority models, which allow you to split a replenishment order into multiple orders with different priorities. For example, you could assign the highest priority (for example, 10) to replenish until the minimum, a lower priority (for example, 30) to replenish until the reorder point, and an even lower priority (for example, 50) to replenish until maximum.

### Q: In the example where a planned purchase order was generated, how will Supply Chain Management peg the purchase order quantity?

DDMRP does not use pegging when it generates planned orders. This is one of the key concepts of DDMRP. Decoupling points are buffers where supply and demand are decoupled, in other words there is no specific supply for a demand, so no pegging. All the replenishment orders replenish the buffer, which is on-hand.

## Lead time and variability factors

### Q: Does the variability factor refer to lead time or demand?

The variability factor refers to demand variability (in other words, how much does demand fluctuate or how consistent is it).

### Q: How can we classify a lead time as long, medium, or short?

Lead time classification is different for every company. You should start by looking at the lead times for all your items and group them into short, medium, and long. Once you assign a lead time factor to each item, you can test and adjust the factor to identify the optimal value.

## Qualified demand

### Q: What is "Spike" demand?

Spikes refer to dates in the future where the total amount of demand exceeds the specified order spike threshold. This indicates that the demand for that date is higher than what is considered normal and will be included in the net flow calculation as part of the qualified demand.

### Q: How is the order spike threshold determined? Is it calculated or defined manually?

The order spike threshold is set manually on the item coverage record.

### Q: Is there a time fence for qualified demand (looking forward)?

The time fence for qualified demand is determined by the coverage time fence setting.
