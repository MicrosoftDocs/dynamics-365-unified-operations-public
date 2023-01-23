---
title: DDMRP FAQ
description: This topic provides answers to frequently asked questions (FAQ) about Demand Driven Material Requirements Planning (DDMRP) in Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: faq
ms.date: 11/24/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# DDMRP FAQ

This topic provides answers to frequently asked questions (FAQ) about Demand Driven Material Requirements Planning (DDMRP) in Microsoft Dynamics 365 Supply Chain Management.

## General

### Does DDMRP require Planning Optimization?

Yes, DDMRP functionality requires the Planning Optimization Add-in for Dynamics 365 Supply Chain Management. It isn't available for the [deprecated master planning engine](../deprecated-master-planning-overview.md). For more information about Planning Optimization, see [Get started with master planning](get-started.md).

### Can priority-based planning be used together with DDMRP?

DDMRP uses priority-based planning functionality to set the priority of planned orders. It calculates the priority of each order by determining the net flow based on the maximum inventory level. Master planning then uses the order priority (instead of the requirement date) to drive supply allocation.

### DDMRP seems to be an extension of the min/max coverage code functionality. Are there any scenarios where I might still use min/max functionality instead of DDMRP when I produce or procure stock?

One of the key differences between min/max and DDMRP is that DDMRP doesn't consider all future net requirements when it's determining whether to reorder. DDMRP is run daily and looks only at past-due demand (today's demand) and order spikes to determine whether an order must be placed immediately. By contrast, min/max looks at all demand in the coverage time fence. It will propose planned orders farther in the future, based on when net requirements will deplete inventory below the minimum point.

### Can I run the existing material requirements planning (MRP) functionality together with DDMRP (for example, when I use coverage groups)?

Yes, we expect that companies will run some combination of decoupling points and other coverage methods (such as min/max, period, or requirement). Decoupling points should be put at strategic points in the supply chain but probably aren't the best answer for every product. Therefore, it's likely that companies will run DDMRP together with other coverage methods.

### Can I simulate DDMRP by using the past two years of data in Supply Chain Management?

Unfortunately not. However, you can easily create an Excel worksheet that contains the formulas, and then use that worksheet to determine what the system would have created as the buffer values.

### Can Supply Chain Management analyze whether an item is in the correct coverage group (for example, to test whether the factors that I set up for variability, and so on, will still meet my item consumption)?

No automated functionality for this purpose currently exists in Supply Chain Management. However, you can manually review the performance of your net flow and on-hand inventory by using the buffer values chart. This chart will help you determine whether your actual net flow and on-hand inventory values are in the zones that you expect them to be in.

### Is there a data entity for importing usage history from legacy enterprise resource planning (ERP) systems?

Yes, if you come from another system and want to keep your past buffer value history, there's a data entity for updating that history.

### Does DDMRP work with Supply Chain Management process manufacturing?

Yes, DDMRP works with any functionality that the deprecated master planning engine works with, provided that you're using Planning Optimization.

### Can DDMRP work with projects?

Yes, DDMRP works with any functionality that the deprecated master planning engine works with, provided that you're using Planning Optimization.

### Does DDMRP work in an intercompany scenario?

Yes, DDMRP works with any functionality that the deprecated master planning engine works with, provided that you're using Planning Optimization.

## The Demand Driven Institute

### Is the Demand Driven Institute part of Microsoft?

No, the Demand Driven Institute is a separate organization that developed the DDMRP methodology. Microsoft developed the functionality that supports the DDMRP methodology in Supply Chain Management, and our solution has been certified by the Demand Driven Institute. For more information, see the [Demand Driven institute website](https://www.demanddriveninstitute.com/).

### Which Demand Driven Institute certifications are recommended for consulting teams?

The recommended certification for consulting teams is Demand Driven Planner (DDP). This certification includes all the DDMRP material and provides a deep understanding of DDMRP principles, to help consultants successfully explain and implement DDRMP in Supply Chain Management.

## Decoupling points

### How can I decide where to define decoupling points?

When you're choosing where to put decoupling points in your supply chain, consider the following factors:

- **External variability** – Add buffers to mitigate effects that can arise from supply variability that's out of your control.
- **Inventory leverage and flexibility** – Add buffers to prioritize items that are used as components in multiple products.
- **Critical operation protection** – Add buffers before critical operations or bottlenecks, to ensure that operations don't sit idle because of a lack of raw materials.
- **Customer tolerance time** – Add buffers at stages where customers expect a short lead time for the item.
- **Sales order visibility horizon** – Add buffers at points where you must quickly react to meet new demand.
- **Market potential lead time** – Add buffers at points where you can sell items at a higher price if the lead time is shorter.

For more information, see [Inventory positioning](ddmrp-inventory-positioning.md).

### Are negative and positive days considered for coverage code decoupling points?

No, the DDMRP model doesn't consider negative and positive days.

### Decoupling points can be added only at the item coverage level. Should I continue to indicate the coverage group at the item level, so that it can be considered for other locations that aren't specified in the item coverage?

Yes, it's possible that not all locations for a given item must be set up as decoupling points. Therefore, you can choose to have a coverage group for an item that uses min/max, period, requirement, and so on, and then indicate the specific decoupling points on the item coverage page. The settings on the item coverage page override the item-level coverage group.

### Is the new coverage code compatible with all product and storage dimensions?

Yes, the *decoupling point* coverage code works with all products and storage dimensions. You must specify all the dimensions for a product that's a decoupling point.

### Do I have to create item coverage records for every variant of a product, or can the calculation be run on product masters?

Decoupling points must be set at the product variant level because each variant will have its own demand pattern, and planned orders are generated at the variant level.

## Planned order generation with DDMRP

### Does DDMRP plan based on forecast values unless qualified demand (orders) for the time frame exceeds the forecast?

DDMRP doesn't use forecasts to generate planned orders. Planned orders are created when the net flow is below the reorder point.

Forecasts are used when the system is set to calculate average daily usage (ADU) based on a *Forward* or *Blended* time period. ADU is one of the factors that affect the buffer values (minimum, reorder point, and maximum). Therefore, it indirectly affects how much you reorder.

### How is production scheduling done when a manufactured part uses DDMRP?

Planned production orders are generated and assigned a priority value that's calculated by dividing the net flow by the maximum inventory level. Master planning then uses the order priority (instead of the requirement date) to schedule production.

### If I set up a maximum reorder quantity that's lower than the reorder quantity, will DDMRP generate multiple planned orders that have different priority values?

The default order settings are respected when planned orders are created, and the same priority will be assigned to all planned orders.

If different priorities must be assigned to different parts, use planning priority models. Planning priority models let you split a replenishment order into multiple orders that have different priorities. For example, you can assign the highest priority (for example, *10*) to replenish until the minimum, a lower priority (for example, *30*) to replenish until the reorder point, and an even lower priority (for example, *50*) to replenish until the maximum.

### In cases where a planned purchase order was generated, how will Supply Chain Management peg the purchase order quantity?

One key concept of DDMRP is that it doesn't use pegging when it generates planned orders. Decoupling points are buffers where supply and demand are decoupled. In other words, there's no specific supply for a demand. Therefore, there's no pegging. All replenishment orders replenish the buffer, which is on-hand inventory.

## Lead time and variability factors

### Does the variability factor refer to lead time or demand?

The variability factor refers to demand variability (in other words, how much demand fluctuates or how consistent it is).

### How can we classify a lead time as long, medium, or short?

Lead time classification differs for every company. You should start by looking at the lead times for all your items, and group them based on whether their lead time is short, medium, or long. After you assign a lead time factor to each item, you can test and adjust the factor to identify the optimal value.

## Qualified demand

### What is spike demand?

Spikes refer to dates in the future when the total amount of demand exceeds the specified order spike threshold. This situation indicates that the demand for a date exceeds what's considered normal and will be included in the net flow calculation as part of the qualified demand.

### How is the order spike threshold determined? Is it calculated or manually defined?

The order spike threshold is manually set on the item coverage record.

### Is there a time fence for qualified demand (looking forward)?

The time fence for qualified demand is determined by the coverage time fence setting.
