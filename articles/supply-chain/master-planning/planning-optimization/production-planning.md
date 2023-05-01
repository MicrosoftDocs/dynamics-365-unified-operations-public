---
title: Production planning
description: This article describes planning for production and explains how to modify planned production orders by using Planning Optimization.
author: t-benebo
ms.date: 08/09/2022
ms.topic: article
ms.search.form: ReqCreatePlanWorkspace
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2020-12-15
ms.dyn365.ops.version: 10.0.13
---

# Production planning

[!include [banner](../../includes/banner.md)]

The following video gives a short introduction to some of the concepts discussed in this article: [Dynamics 365 Supply Chain Management: Planning Optimization enhancements](https://youtu.be/u1pcmZuZBTw).

## Turn this feature on or off for your system

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Planned production orders for Planning Optimization* feature in the [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Planned production orders

When master planning creates planned orders to fulfill requirements, the order type is determined by the value of the **Planned order type** field. If the **Planned order type** field is set to *Production*, planned production orders are created. These planned production orders include information about the active bill of materials (BOM) and the route ID from the related production setup.

## Requirements from BOMs

BOM information is honored during master planning. The plan output includes material supply to cover related material demand for production.

During master planning, the current, active BOM is used to determine the materials that are required for production. This step is done through all levels of the BOM structure that is related to the required production order. Material requirement is fulfilled by using available on-hand inventory, existing on-order supply, and approved planned orders. If additional material is required anywhere, a planned order is created to cover the demand.

## Scheduling during firming

Planned production orders include the route ID that is required for production scheduling. However, scheduling support during the planning run for planned orders is pending. The route ID is used to schedule planned production orders during firming. Therefore, the lead time on planned production orders can differ from the lead time on related scheduled, firmed production orders that are generated from them, as described here:

- **Planned production order** – The lead time is based on the static lead time from the released product.
- **Firmed production order** – The lead time is based on scheduling that uses route information and related resource constraints.

## Delays

If the lead time for required material is longer than the period between today's date and the material requirement date, the planned order for the required material and the related production order will be delayed. For planned orders, the delay (in days) is calculated based on the lead time from the released product. The delay information is then propagated through all levels of the BOM structure. Therefore, you can follow the impact of delayed raw material all the way to the customer sales order.

## Modifying planned orders

When you change information on a planned order, you receive the following message: "Note that the impact of manual changes on planned orders won't be reflected in the rest of the plan until the next master planning run."

If you want to change information on a planned order and see the impact on the related material requirements, follow these steps.

1. Update the planned order.
2. Approve the planned order.
3. Run master planning.

When you run master planning, you should not use filters if planned production orders are included. For more information, see the [Filters](#filters) section later in this article.

> [!NOTE]
> If the delivery date of the planned order is changed to a later date, the demand might be pegged against a new planned order. This behavior occurs when the new supply date causes a delay for the pegged demand but, according to the lead time settings, the delay can be avoided.

## Explosion page

You can use the **Explosion** page to analyze the demand that is required for a specific production order or planned production order, the related coverage, and pegging information. Information on the **Explosion** page is updated during master planning. You can't update the information directly from the **Explosion** page.

## <a name="filters"></a>Filters

To ensure that master planning has the information that it needs to calculate the correct result, you must include all products that have any relation to products in the whole BOM structure of the planned order. For planning scenarios that include production, we therefore recommend that you avoid filtered master planning runs.

Although dependent child items are automatically detected and included in master planning runs when the deprecated master planning engine is used, Planning Optimization doesn't currently perform this action.

For example, if a single bolt from the BOM structure of product A is also used to produce product B, all products in the BOM structure of products A and B must be included in the filter. Because it can be complex to ensure that all products are part of the filter, we recommend that you avoid filtered master planning runs when production orders are involved. Otherwise, master planning will provide undesired results.

### Reasons to avoid filtered master planning runs

When you run filtered master planning for a product, Planning Optimization (unlike the deprecated master planning engine) doesn't detect all the subproducts and raw materials in the BOM structure of that product, and therefore doesn't include them in the master planning run. Even though Planning Optimization identifies the first level in the BOM structure of the product, it doesn't load any product settings (such as the default order type or item coverage) from the database.

In Planning Optimization, data for the run is loaded beforehand and applies the filters. This means that if a subproduct or raw material included in a specific product isn't part of the filter, information about it won't be captured for the run. Additionally, if the subproduct or raw material is also included in another product, then a filtered run that includes only the original product and its components would remove existing planned demand that was created for that other product.

This logic may cause filtered master planning runs to produce unexpected results. The following sections provide examples that illustrate the unexpected results that could occur.

### Example 1

Finished good *FG* consists of following components:

- Raw material *R*
- Subproduct *S1*, which consists of subproduct *S2*

There is inventory on-hand for the raw material *R*, while subproduct *S1* isn't present in the inventory.

When you do a filtered master planning run for finished good *FG*, you will get a planned production order for the finished good *FG*, a planned purchase order for the raw material *R*, and a planned purchase order for the subproduct *S1*. This is an undesirable result because Planning Optimization has ignored existing supply for raw material *R* and subproduct *S1* needs to be produced using *S2* rather than ordered directly. This happened because Planning Optimization only has the list of components for the finished good *FG* without any related information, such as the existing supply of its components or their default order settings.

### Example 2

Building on the previous example, an additional finished good, *FG2*, also uses subproduct *S1*. A planned order exists for finished good *FG2* and planned demand exists for all of its components, including *S1*.

You decide to overcome the undesired results of the filtered master planning run from the previous example by adding all the subproducts and raw materials from the BOM structure of finished good *FG* to the filter and then running full regeneration.

When you run the full regeneration, the system deletes all existing results for all the included products and then recreates results based on the new calculations. This means that existing planned demand for product *S1* is deleted and then recreated taking into account finished good *FG* requirements only, while finished good *FG2* requirements are disregarded. This happens because when you run Planning Optimization, it doesn't include the planned demand of other planned production orders&mdash;only the planned demand generated during the run is used.

> [!NOTE]
> If the existing planned order for finished good *FG2* is in status *Approved*, then the approved planned demand will be included, even when the parent product isn't added to the filter.

Therefore, unless you add all the components of the finished good *FG*, finished good *FG2*, and all other products that these components are part of (together with their components), the filtered master planning run will provide undesired results.

Because it can be complex to ensure that all products are part of the filter, we recommend that you avoid filtered master planning runs when production orders are involved.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
