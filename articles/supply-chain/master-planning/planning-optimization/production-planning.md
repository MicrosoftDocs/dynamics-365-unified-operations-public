---
# required metadata

title: Production planning
description: This topic describes planning for production and explains how to modify planned production orders by using Planning Optimization.
author: ChristianRytt
manager: tfehr
ms.date: 12/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
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

<!-- The following video gives a short introduction to some of the current capabilities. 
KFM: Link to video for production functionality, coming soon... -->

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

Although dependent child items are automatically detected and included in master planning runs when the built-in master planning engine is used, Planning Optimization doesn't perform this action.

For example, if a single bolt from the BOM structure of product A is also used to produce product B, all products in the BOM structure of products A and B must be included in the filter. Because it can be very complex to ensure that all products are part of the filter, we recommend that you avoid filtered master planning runs when production orders are involved.
