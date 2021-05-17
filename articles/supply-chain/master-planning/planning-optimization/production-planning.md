---
# required metadata

title: Production planning
description: This topic describes planning for production and explains how to modify planned production orders by using Planning Optimization.
author: ChristianRytt
ms.date: 12/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-12-15
ms.dyn365.ops.version: 10.0.13

---
# Production planning

Planning Optimizations supports several production scenarios. If you're migrating from the existing, built-in master planning engine, it's important that you be aware of some changed behavior.

The following video gives a short introduction to some of the concepts discussed in this topic: [Dynamics 365 Supply Chain Management: Planning Optimization enhancements](https://youtu.be/u1pcmZuZBTw).

## Turn on this feature for your system

If your system doesn't already include the features described in this topic, go to [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Planned production orders for Planning Optimization* feature.

## Planned production orders

When master planning creates planned orders to fulfill requirements, the order type is determined by the value of the **Planned order type** field. If the **Planned order type** field is set to *Production*, planned production orders are created. These planned production orders include information about the active bill of materials (BOM) and the route ID from the related production setup.

## Requirements from BOMs

BOM information is honored during master planning. The plan output includes material supply to cover related material demand for production.

During master planning, the current, active BOM is used to determine the materials that are required for production. This step is done through all levels of the BOM structure that is related to the required production order. Material requirement is fulfilled by using available on-hand inventory, existing on-order supply, and approved planned orders. If additional material is required anywhere, a planned order is created to cover the demand.

## Scheduling during firming

Planned production orders include the route ID that is required for production scheduling. However, scheduling support during the planning run for planned orders is pending. The route ID is used to schedule planned production orders during firming. Therefore, the lead time on planned production orders can differ from the lead time on related scheduled, firmed production orders that are generated from them, as described here:

- **Planned production order** – The lead time is based on the static lead time from the released product.
- **Firmed production order** – The lead time is based on scheduling that uses route information and related resource constraints.

For more information about expected feature availability, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

If you depend on production functionality that isn't yet available for Planning Optimization, you can continue to use the built-in master planning engine. No exception is required.

## Delays

If the lead time for required material is longer than the period between today's date and the material requirement date, the planned order for the required material and the related production order will be delayed. For planned orders, the delay (in days) is calculated based on the lead time from the released product. The delay information is then propagated through all levels of the BOM structure. Therefore, you can follow the impact of delayed raw material all the way to the customer sales order.

## Modifying planned orders

When you change information on a planned order, you receive the following message: "Note that the impact of manual changes on planned orders won't be reflected in the rest of the plan until the next master planning run."

If you want to change information on a planned order and see the impact on the related material requirements, follow these steps.

1. Update the planned order.
2. Approve the planned order.
3. Run master planning.

When you run master planning, you should not use filters if planned production orders are included. For more information, see the [Filters](#filters) section later in this topic.

> [!NOTE]
> If the delivery date of the planned order is changed to a later date, the demand might be pegged against a new planned order. This behavior occurs when the new supply date causes a delay for the pegged demand but, according to the lead time settings, the delay can be avoided.

## Explosion page

You can use the **Explosion** page to analyze the demand that is required for a specific production order or planned production order, the related coverage, and pegging information. Information on the **Explosion** page is updated during master planning. You can't update the information directly from the **Explosion** page.

## <a name="filters"></a>Filters

For planning scenarios that include production, we recommend that you avoid filtered master planning runs. To ensure that Planning Optimization has the information that is required to calculate the correct result, you must include all products that have any relation to products in the whole BOM structure of the planned order.

Although dependent child items are automatically detected and included in master planning runs when the built-in master planning engine is used, Planning Optimization does not perform this action.

For example, if a single bolt from the BOM structure of product A is also used to produce product B, all products in the BOM structure of products A and B must be included in the filter. Because it can be very complex to ensure that all products are part of the filter, we recommend that you avoid filtered master planning runs when production orders are involved. Otherwise, master planning will provide undesired results.

Let us review reasons for avoiding filtered master planning runs in detail.

When you run filtered master planning for a product, Planning Optimization, in a contrast to built-in master planning engine, does not detect all the sub products and raw materials in the BOM structure of that product and thus does not include them into the master planning run. Even though Planning Optimization identifies the first level in the BOM structure of the product, it does not load any product settings, like default order type or item coverage, from the database.

In Planning Optimization, data for the run is loaded beforehand, considering filters. It means that if a sub product or raw material that is included in a specific product is not part of the filter, information about it will not be captured for the run. And if the sub product or raw material is also included in another product, then filtered run that includes only the original product and its components would remove existing planned demand created for another product.

Logic described above may lead to unexpected results of the filtered master planning runs. Below you can find examples that illustrate unexpected results that you may get.

### Example 1:

Finished good FG consists of following components: raw material R and sub product S1 that consists of sub product S2. There is inventory on-hand for the raw material R, while product S1 is not present in the inventory.

When you run a filtered master planning for the product FG you will get a planned production order for the product FG, a planned purchase order for the raw material R and a planned purchase order for the sub product S1.

The result is not desired since Planning Optimization has ignored existing supply for raw material R and the fact that product S1 needs to be produced. This happened because Planning Optimization has just the list of components of the product FG without any related information like existing supply of the components or their default order settings.

### Example 2:

Here additional finished good FG2 also uses sub product S1. A planned order exists for product FG2 and planned demand for all its components including S1.

You decide to overcome undesired results of the filtered master planning run described above by adding all the sub products and raw materials from the BOM structure of the product FG to the filter and running full regeneration.

When full regeneration is run, all existing results for all the products included get deleted and then recreated based on new calculations. It means that existing planned demand for product S1 is deleted and then recreated taking into account finished good FG requirements only, while finished good FG2 requirements are disregarded. It happened because when Planning Optimization is run, it does not include the planned demand of other planned production orders; only the planned demand which is generated during the run is used.

> [!NOTE]
> If the existing planned order for product FG2 is in status Approved, then the approved planned dmemand will be included, even when the parent product is not added to the filter.

Therefore, unless you add all the components of the product FG, product FG2 and all other products that these components are part of (together with their components), the filtered master planning run will provide undesired results.

Because it can be very complex to ensure that all products are part of the filter, we recommend that you avoid filtered master planning runs when production orders are involved.

It is important to note that we are planning improved filtering support for production scenarios for a future release.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]