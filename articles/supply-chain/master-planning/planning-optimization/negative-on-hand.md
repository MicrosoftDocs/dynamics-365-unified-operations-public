---
title: Planning with negative on-hand quantities
description: Learn how negative on-hand is handled, including a step-by-step process describing how functionality works and various examples. 
author: Henrikan
ms.author: henrikan
ms.topic: how-to
ms.date: 05/05/2026
ms.custom:
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: ReqCreatePlanWorkspace
---

# Planning with negative on-hand quantities

[!include [banner](../../includes/banner.md)]

If the system shows a negative aggregate on-hand quantity, the planning engine treats the quantity as 0 to help avoid over-supply. Here's how this functionality works:

1. Master planning aggregates on-hand quantities at the lowest level of coverage dimensions. For example, if *location* isn't a coverage dimension, master planning aggregates on-hand quantities at the *warehouse* level.
1. If the aggregate on-hand quantity at the lowest level of coverage dimensions is negative, the system assumes that the on-hand quantity is really 0.

> [!IMPORTANT]
> The planning system is only as precise as the input data. If the input data is inaccurate, negative on-hand records indicate that the inventory information in Microsoft Dynamics 365 Supply Chain Management is out of sync with the real world. Therefore, the planning result is flawed. To get a precise planning result, minimize the number of records that show a negative on-hand quantity.

## Example 1

Warehouse 13 is configured in the following manner:

- **Coverage code:** Min./Max.
- **Minimum:** 15 pieces (pcs.)
- **Maximum:** 25 pcs.

The lowest level of coverage dimensions is *warehouse*, and the following on-hand quantities are recorded at the *location* level:

- **Site 1, warehouse 13, location 1:** 20 pcs.
- **Site 1 warehouse 13, location 2:** &minus;8 pcs.

Therefore, the aggregate on-hand quantity for warehouse 13 is 12 pcs. (= 20 pcs. &minus; 8 pcs.).

In this case, the planning engine uses an aggregate on-hand quantity of 12 pcs. for warehouse 13.

The result is a planned order of 13 pcs. (= 25 pcs. &minus; 12 pcs.) to refill warehouse 13 from 12 pcs. to 25 pcs.

## Example 2

Warehouse 13 is configured in the following manner:

- **Coverage code:** Min./Max.
- **Minimum:** 15 pcs.
- **Maximum:** 25 pcs.

The lowest level of coverage dimensions is *warehouse*, and the following on-hand quantities are recorded at the *location* level:

- **Site 1, warehouse 13, location 1:** 4 pcs.
- **Site 1 warehouse 13, location 2:** &minus;8 pcs.

Therefore, the aggregate on-hand quantity for warehouse 13 is &minus;4 pcs. (= 4 pcs. &minus; 8 pcs.). In other words, it's less than 0 (zero).

In this case, the planning engine assumes that the on-hand quantity for warehouse 13 is 0 pcs. instead of &minus;4 pcs.

The result is a planned order of 25 pcs. (= 25 pcs. &minus; 0 pcs.) to refill warehouse 13 from 0 pcs. to 25 pcs.

## Planning when there is a reservation against negative on-hand inventory

If you adjust inventory while physical reservations exist, you can cause a situation where an order is physically reserved against negative inventory. In this case, because a physical reservation exists, you need to have supply to cover the reserved quantity. Therefore, replenishment is required, so the system will either create a planned order to replenish the quantity that couldn't be covered by the existing on-hand inventory, or cover it with an existing order for the item.

The following example illustrates this scenario.

### Example

The system is configured in the following way:

- Product *FG* exists and has *10* pcs. of on-hand inventory.
- The product configuration allows for physical negative inventory.
- A sales order exists for a quantity of *10* pcs. of product *FG*.
- The sales order quantity is physically reserved against existing on-hand inventory.

You then adjust the quantity of product *FG* so that the on-hand inventory becomes 5. Because the on-hand product inventory is 5, the sales order quantity is now reserved against quantity that isn't available on-hand (it would be similar if on-hand were 0, in which case the sales order would be reserved against negative inventory). If you run master planning now, a planned order of quantity 5 for *FG* is created to supply the sales order, because master planning always uses existing supply or creates a new planned order to supply the physical reservation.

## Handle negative on-hand with coverage groups

Because Planning Optimization treats negative aggregate on-hand as 0, you might need to configure your coverage groups to ensure that inventory is replenished to the levels your business requires. To control how the system responds to negative on-hand scenarios, define minimum and maximum quantities in item coverage groups.

To configure coverage groups for handling negative on-hand, follow these steps:

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. Select or create a coverage group, and then set the **Coverage code** field to *Min/Max*.
1. Go to **Master planning** \> **Master planning** \> **Setup** \> **Coverage** \> **Item coverage** for the relevant items.
1. Set the **Minimum** field to the lowest inventory level that you want to maintain.
1. Set the **Maximum** field to the target inventory level for replenishment.

When you run master planning, the system creates planned orders to bring inventory back up to the maximum level whenever the projected on-hand falls below the minimum level. This approach helps maintain appropriate inventory levels even when the system encounters negative on-hand quantities.

Learn more about coverage codes and how each replenishment method works in [Coverage settings](../../coverage-settings.md).

## Related information

- [Differences between Planning Optimization and the deprecated master planning engine](planning-optimization-differences-with-built-in.md)
- [Coverage settings](../../coverage-settings.md)
- [Safety stock fulfillment for items](../../safety-stock-replenishment.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
