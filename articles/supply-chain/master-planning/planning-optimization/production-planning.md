---
title: Production planning
description: Learn about planning for production and explains how to modify planned production orders by using Planning Optimization.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/06/2026
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

> [!NOTE]
> If you change the delivery date of the planned order to a later date, the demand might peg against a new planned order. This behavior occurs when the new supply date causes a delay for the pegged demand but, according to the lead time settings, the delay can be avoided.

## Explosion page

Use the **Explosion** page to analyze the demand that is required for a specific production order or planned production order, the related coverage, and pegging information. The system updates information on the **Explosion** page during master planning. You can't update the information directly from the **Explosion** page.

## <a name="filters"></a>Filters

Planning Optimization offers advanced filtering options that can apply at the plan level, runtime level, or both. To learn more about the various filter options, see [Run planning for a subset of items](plan-filters.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
