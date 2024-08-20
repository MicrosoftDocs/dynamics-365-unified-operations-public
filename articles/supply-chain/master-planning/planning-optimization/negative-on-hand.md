---
title: Planning with negative on-hand quantities
description: Learn how negative on-hand is handled, including a step-by-step process describing how functionality works and various examples. 
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 07/22/2021
ms.custom:
ms.reviewer: kamaybac 
ms.search.form: ReqCreatePlanWorkspace
---

# Planning with negative on-hand quantities

[!include [banner](../../includes/banner.md)]

If the system shows a negative aggregate on-hand quantity, the planning engine treats the quantity as 0 (zero) to help avoid over-supply. Here is how this functionality works:

1. Master planning aggregates on-hand quantities at the lowest level of coverage dimensions. (For example, if *location* isn't a coverage dimension, master planning aggregates on-hand quantities at the *warehouse* level.)
1. If the aggregate on-hand quantity at the lowest level of coverage dimensions is negative, the system assumes that the on-hand quantity is really 0 (zero).

> [!IMPORTANT]
> The planning system can be only as precise as the input data. If the input data is inaccurate, negative on-hand records will indicate that the inventory information in Microsoft Dynamics 365 Supply Chain Management is out of sync with the real world. Therefore, the planning result will be flawed. To get a precise planning result, you should minimize the number of records that show a negative on-hand quantity.

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

You then adjust the quantity of product *FG* so that the on-hand inventory becomes 5. Because the on-hand product inventory is 5, the sales order quantity is now reserved against quantity that is not available on-hand (it would be similar if on-hand were 0, in which case the sales order would be reserved against negative inventory). If you run master planning now, a planned order of quantity 5 for *FG* will be created to supply the sales order, because master planning will always use existing supply or create a new planned order to supply the physical reservation.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
