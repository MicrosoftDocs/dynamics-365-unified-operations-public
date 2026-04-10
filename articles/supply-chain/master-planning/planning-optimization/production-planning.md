---
title: Production planning
description: Learn about planning for production and explains how to modify planned production orders by using Planning Optimization.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 03/25/2026
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace
---

# Production planning

[!include [banner](../../includes/banner.md)]

The following video provides a short introduction to some of the concepts discussed in this article: [Dynamics 365 Supply Chain Management: Planning Optimization enhancements](https://youtu.be/u1pcmZuZBTw).

## Planned production orders

When master planning creates planned orders to fulfill requirements, the value of the **Planned order type** field determines the order type. If you set the **Planned order type** field to *Production*, the system creates planned production orders. These planned production orders include information about the active bill of materials (BOM) and the route ID from the related production setup.

## Requirements from BOMs

Master planning uses BOM information. The plan output includes material supply to cover related material demand for production.

During master planning, the system uses the current, active BOM to determine the materials required for production. The system checks all levels of the BOM structure that relate to the required production order. The system fulfills material requirements by using available on-hand inventory, existing on-order supply, and approved planned orders. If the system finds that additional material is required, it creates a planned order to cover the demand.

When the system searches for an appropriate BOM version to use for an item in a coverage group that has the **[Use the specified BOM or formula version](../coverage-settings.md)** option turned off, it takes several parameters into account. These parameters include the validity period of the BOM version, whether the BOM version is active or approved, and the applicable quantity. The system doesn't reconsider the chosen BOM version after a receipt is scheduled in cases where a planned production order is delayed or scheduled to start earlier or later.

When you replenish a BOM component by using a production or batch order, the validity date that the system uses to search for the applicable BOM or formula version is determined after the system schedules its parent order. The validity date is based on the scheduled start or end date of an operation from the parent planned production order schedule (by default, the start date of the first operation). The system determines the scheduled start and end dates after it schedules the parent production order. If the system delays the parent planned production order later in the planning process and must push forward its scheduled start or end date times because a subcomponent order is delayed, the system doesn't reconsider the BOM version for the subcomponent. The BOM version is still based on the original scheduling attempt (backward in most cases) of the parent planned production order.

Individual BOM lines also have validity periods. The system evaluates these periods after it schedules a planned production order, so it uses the corresponding operation start or end dates to check for validity. Even though a BOM version and its lines might have the same validity periods, the system uses different dates to evaluate them. For a BOM version, the system uses the demand requirement date. For a BOM line, the system uses the scheduled start of the planned production order for the finished good.

The system takes the following actions:

1. Create a planned production order to replenish demand and select a BOM version to use.
1. Schedule the order without reevaluating the BOM version, even if the date shifts as a result of scheduling.
1. Assess the BOM lines for the selected BOM version to ensure they're valid for the scheduled dates.
1. Create BOM line requirements for the valid BOM lines only.
1. If required by the planning settings, cover BOM line requirements with supply down to the specific BOM level.
1. Evaluate whether supply of the lower BOM levels affects the delivery schedule for any parent production orders and adjust the schedules accordingly.

## Scheduling during firming

Planned production orders include the route ID that is required for production scheduling. However, scheduling support during the planning run for planned orders is pending. The route ID is used to schedule planned production orders during firming. Therefore, the lead time on planned production orders can differ from the lead time on related scheduled, firmed production orders that are generated from them.

- **Planned production order** – The lead time is based on the static lead time from the released product.
- **Firmed production order** – The lead time is based on scheduling that uses route information and related resource constraints.

## Delays

If the lead time for required material is longer than the period between today's date and the material requirement date, the planned order for the required material and the related production order are delayed. For planned orders, the system calculates the delay (in days) based on the lead time from the released product. The system then propagates the delay information through all levels of the BOM structure. Therefore, you can follow the impact of delayed raw material all the way to the customer sales order.

## Modifying planned orders

When you change information on a planned order, you receive the following message: "Note that the impact of manual changes on planned orders won't be reflected in the rest of the plan until the next master planning run."

If you want to change information on a planned order and see the impact on the related material requirements, follow these steps:

1. Update the planned order.
1. Approve the planned order.
1. Run master planning.

When you run master planning, don't use filters if planned production orders are included. Learn more in the [Filters](#filters) section later in this article.

> [!NOTE]
> If you change the delivery date of the planned order to a later date, the demand might peg against a new planned order. This behavior occurs when the new supply date causes a delay for the pegged demand but, according to the lead time settings, the delay can be avoided.

## Explosion page

Use the **Explosion** page to analyze the demand that is required for a specific production order or planned production order, the related coverage, and pegging information. The system updates information on the **Explosion** page during master planning. You can't update the information directly from the **Explosion** page.

## <a name="filters"></a>Filters

To ensure that master planning has the information it needs to calculate the correct result, include all products that relate to products in the whole BOM structure of the planned order. For planning scenarios that include production, avoid filtered master planning runs.

Although the deprecated master planning engine automatically detects and includes dependent child items in master planning runs, Planning Optimization doesn't currently perform this action.

For example, if a single bolt from the BOM structure of product A is also used to produce product B, include all products in the BOM structure of products A and B in the filter. Because it can be complex to ensure that all products are part of the filter, avoid filtered master planning runs when production orders are involved. Otherwise, master planning provides undesired results.

### Reasons to avoid filtered master planning runs

When you run filtered master planning for a product, Planning Optimization (unlike the deprecated master planning engine) doesn't detect all the subproducts and raw materials in the BOM structure of that product, and therefore doesn't include them in the master planning run. Even though Planning Optimization identifies the first level in the BOM structure of the product, it doesn't load any product settings (such as the default order type or item coverage) from the database.

In Planning Optimization, the system loads data for the run beforehand and applies the filters. This process means that if a subproduct or raw material included in a specific product isn't part of the filter, the run doesn't capture information about it. Additionally, if the subproduct or raw material is also included in another product, then a filtered run that includes only the original product and its components removes existing planned demand that was created for that other product.

This logic might cause filtered master planning runs to produce unexpected results. The following sections provide examples that illustrate the unexpected results that could occur.

### Example 1

Finished good *FG* consists of the following components:

- Raw material *R*
- Subproduct *S1*, which consists of subproduct *S2*

There's inventory on hand for the raw material *R*, while subproduct *S1* isn't present in the inventory.

When you run a filtered master planning run for finished good *FG*, you get a planned production order for the finished good *FG*, a planned purchase order for the raw material *R*, and a planned purchase order for the subproduct *S1*. This result is undesirable because Planning Optimization ignored existing supply for raw material *R* and subproduct *S1* needs to be produced using *S2* rather than ordered directly. This result happened because Planning Optimization only has the list of components for the finished good *FG* without any related information, such as the existing supply of its components or their default order settings.

### Example 2

Building on the previous example, an additional finished good, *FG2*, also uses subproduct *S1*. A planned order exists for finished good *FG2* and planned demand exists for all of its components, including *S1*.

You decide to overcome the undesired results of the filtered master planning run from the previous example by adding all the subproducts and raw materials from the BOM structure of finished good *FG* to the filter and then running full regeneration.

When you run the full regeneration, the system deletes all existing results for all the included products and then recreates results based on the new calculations. This process means that the system deletes existing planned demand for product *S1* and then recreates it taking into account finished good *FG* requirements only, while finished good *FG2* requirements are disregarded. This situation happens because when you run Planning Optimization, it doesn't include the planned demand of other planned production orders—it only uses the planned demand generated during the run.

> [!NOTE]
> If the existing planned order for finished good *FG2* is in status *Approved*, then the approved planned demand is included, even when the parent product isn't added to the filter.

Therefore, unless you add all the components of the finished good *FG*, finished good *FG2*, and all other products that these components are part of (together with their components), the filtered master planning run provides undesired results.

Because it can be complex to ensure that all products are part of the filter, avoid filtered master planning runs when production orders are involved.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
