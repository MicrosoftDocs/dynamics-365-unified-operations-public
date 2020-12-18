---
# required metadata

title: Production planning
description: This topic describes planning with production and explains how to modify planned production orders with Planning Optimization.
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

Planning Optimizations offers support for several production scenarios. If you are migrating from the existing, built-in master planning engine, it is important to be aware of some changed behaviors.

<!-- The following video gives a short introduction to some of the current capabilities. 
KFM: Link to video for production functionality, coming soon...  -->

## Planned production orders

When master planning creates planned orders to fulfil requirements, the order type is determined by the **Planned order type**. When the **Planned order type** is set to *Production*, planned production orders are created. The planned production order will include active bill of materials (BOM) information and the route ID from the related production setup.

## Requirement from BOM

BOM information is honored during master planning and the plan output includes material supply to cover related material demand for production.

During master planning, the current and active BOM will be used to determine the materials required for production. This is done through all levels of the BOM structure related to the required production order. Material requirement is fulfilled with available on-hand inventory, existing on-order supply, and approved planned orders. Where additional material is required, a planned order is created to cover the demand.

## Scheduling during firming

Planned production orders include the route ID needed for production scheduling. However, scheduling support during the planning run for planned orders is pending. The route ID will be used for scheduling of planned production orders during firming. As a result, the lead time on planned production orders can differ from the related scheduled firmed production order generated from the planned production order as follows:

- **Planned production order** – Lead time is based on static lead time from released product.
- **Firmed production order** – Lead time is based on scheduling with route information and related resource constrains.

For additional information on expected feature availability, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

If you depend on production functionality not yet available with Planning Optimization, you can continue to use the built-in master planning engine&mdash;no exception is required.

## Delays

When lead time for required material is longer than the period between today's date and the material requirement date, the planned order for the required material and the related production order will be delayed. For planned orders, the delay (in days) is calculated based on the lead time from the released product. The delay information is propagated through all levels of the BOM structure, meaning that you can follow the impact of a delayed raw material all the way to the customer sales order.

## Modifying planned orders

When you modify information on a planned order, the following message is shown: &quot;Note that the impact of manual changes on planned orders won't be reflected in the rest of the plan until the next master planning run.&quot;

If you want to change information on a planned order and see the impact on the related material requirements, you should:

1. Update the planned order
2. Approve the planned order
3. Run master planning

When you run master planning, this should be done without filters when including planned production orders (for details, see the [Filters](#filters) section later in this topic).

> [!NOTE]
> If the delivery date of the planned order is changed to a later date, then it can result in the demand being pegged against a new planned order. This happens when the new supply date causes a delay for the pegged demand that could be avoided according to lead time settings.

## The Explosion page

Use the **Explosion** page to analyze the demand required for a specific production or planned production order and the related coverage, as well as for pegging information. Information on the **Explosion** page is updated during master planning. It is not possible to update the information directly from the **Explosion** page.

## <a name="filters"></a>Filters

For planning scenarios that include production, we recommend that you avoid filtered master planning runs. To ensure that Planning Optimization has the information needed to calculate the correct result, you must include all products that have any relation to products in the entire BOM structure of the planned order.

This concept differs from the built-in master planning engine, where dependent child items will automatically be detected and included in the run. This is not the case for Planning Optimization.

**Example**: If a single bolt from the BOM structure of product A is also used to produce product B, then all products in the BOM structure of product A and B must be included in the filter. It can be very complex to ensure that all products are part of the filter, which is why we recommend avoiding filtered master planning runs when production orders are involved.
