---
title: Reserve inventory quantities
description: Learn about the different options that are available for reserving inventory, including an outline on inventory reservation policies.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventModelGroup
ms.topic: how-to
ms.date: 11/24/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Reserve inventory quantities

[!INCLUDE [banner](../includes/banner.md)]

This article describes the different options for reserving inventory.

You can automatically reserve inventory quantities for a specific sales order. This reservation means that you can't withdraw reserved inventory from the warehouse for other orders unless you cancel the inventory reservation or part of the inventory reservation.

There are several reasons for reserving inventory:

- First ordered, first delivered, which means that customers get available items in the same order in which they place their orders.
- Shortage of items due to a long or unknown delivery time from the vendor. You might want to ensure that certain customers or orders get delivery of the first-available items.
- Certain customers and certain types of orders have first priority for delivery.
- Items with serial or batch numbers. You can mark certain items that are or will be delivered to specific orders.
- Specially ordered items that are reserved for certain orders.
- Production orders. For example, you can mark items that are produced for and adjusted to specific orders.

Inventory can be reserved automatically when you create a new order line, or you can reserve inventory manually on the individual orders. You can also reserve inventory at different stages in a production process. Only stocked products can be reserved. You can't reserve services because there's no on-hand inventory. You can reserve both physical on-hand inventory and ordered but not yet received inventory. If you reserve a larger quantity than what the on-hand inventory contains, a message displays that you can't reserve such a large quantity. You can then either reserve the quantity anyway or change the ordered quantity. The quantity can be either reserved or changed. If you reserve more items than are available, the shortage is covered the next time that items are available for delivery.

## Inventory reservation policies

Set inventory reservation policies on the **Item model groups** page, the **Inventory and warehouse management parameters** page, or the **Production parameters** page.

### Policies on the Item model groups page

The **Inventory policies** section contains the following reservation policies.

The policies include settings for sales order reservation, and some settings also affect other order types. The effects depend on the item and batch-tracking setup and on the relevant order line, such as a sales order line or a BOM or formula line.

| Reservation policy | Description |
|---|---|
| FIFO date-controlled | If you select the **FIFO date-controlled** option, a sorting date controls the inventory reservation according to the FIFO principle. Batches are reserved based on the earliest date of receipt of items, following the first in, first out (FIFO) principle. |
| Backward from ship date | This option becomes available if you select the **FIFO date-controlled** option. If you select **Backward from ship date** and you're reserving available physical inventory, the inventory reservation is controlled by the last update physical date according to the FIFO rule. If you're reserving available ordered inventory, the inventory is reserved backward from the desired ship date according to the last in, first out (LIFO) principle. If no receipts are available before the ship date, the reservation follows the LIFO rule using the transaction ship date. |
| Item sales reservation | Determines whether item reservation is manual or automatic. If a reservation is automatic, inventory is reserved when you create order lines. You can make reservations at the item number level for BOMs (**Automatic** option), or for the individual elements of a BOM (**Explosion** option). The default value for **Item sales reservation** might be inherited from **Accounts receivable parameters.** On that page, set the value in the Reservation field in the **Sales default values** **section** on the **General** tab. |
| Same batch selection | Same-batch reservation lets you reserve inventory for a sales order line from a single batch. For production and batch orders, when you enable the requirement on a BOM or formula line, raw-material reservation is limited to one batch for that line. For sales order reservations, you must also set the **Consolidate requirement** option to **Yes**. Additional settings are required for the tracking dimension group and storage dimension group. Learn more in [Reserve the same batch for a sales order](../sales-marketing/reserve-same-batch-sales-order.md). |
| Consolidate requirement | This option is similar to the **Same batch selection** option, and it consolidates inventory that's reserved for sales order lines into a single requirement. |
| FEFO date-controlled | This option allows you to reserve batches that are close to their expiration date or best before date. You also need to set the **Pick criteria** field to select either **Expiration date** or **Best before date**. |

#### Example for FIFO date-controlled and Backward from ship date

In this example, on-hand inventory for item number A exists for three different batch numbers.

| Item number | Batch number | Quantity | Date |
|---|---|---|---|
| A | 1000 | 5 | February 2, 2016 |
| A | 1001 | 3 | January 1, 2016 |
| A | 1002 | 7 | March 3, 2016 |

A sales order that should be automatically reserved and delivered on April 4, 2016, reserves the following batch:

- If you clear both the **FIFO date-controlled** and **Backward from ship date** check boxes, batch 1000 is reserved because it's the batch with the lowest number.
- If you select the **FIFO date-controlled** check box and clear the **Backward from ship date** check box, batch 1001 is reserved because it's the batch with the first date of receipt (FIFO).
- If you select both the **FIFO date-controlled** and **Backward from ship date** check boxes, batch 1002 is reserved because it's the batch receipt closest to the sales order ship date.

### Same-batch selection for production and batch orders

When you require same-batch selection for a raw material, the system restricts available on-hand inventory during reservation to a single batch for the BOM or formula line. This restriction prevents the line's raw-material consumption from splitting across multiple batches. Set the default requirement in the released product's item model group, and override it on individual BOM or formula lines. To learn more, see [same-batch selection for production and batch orders](../production-control/reserve-same-batch-production-order.md).

### Policies on the Inventory and warehouse management parameters page

The **Inventory and warehouse management parameters** page has two options related to reservations:

- Use the **Reserve ordered items** option on the **General** tab to reserve item receipts that you ordered against item issues in Accounts receivable, Project management and accounting, and Production control. If you clear this option, you can only reserve items that you physically received. If you set up a particular item to accept negative inventory, this field isn't relevant.
- The **Reserve items automatically** option on the **Transfer** tab determines the default setting for automatically reserving items for transfer orders. You can override the default setting on individual transfer orders.

### Inventory reservation policies on the Production parameters page

The value of the **Reservation** field on the **General** tab on the **Production parameters** page determines the default point in the production process at which inventory should be reserved. For example, you can reserve inventory when work is scheduled or when work is started.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
