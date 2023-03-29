---
# required metadata

title: Reserve inventory quantities
description: This article describes the different options that are available for reserving inventory.
author: yufeihuang
ms.date: 06/20/2017
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventModelGroup
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 207264
ms.assetid: 47537e4f-cdf6-4813-96fd-c945b2dfe9d4
ms.search.region: Global
# ms.search.industry:
ms.author: yufeihuang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Reserve inventory quantities

[!include [banner](../includes/banner.md)]

This article describes the different options that are available for reserving inventory.

You can automatically reserve inventory quantities for a specific sales order. This means that reserved inventory can't be withdrawn from the warehouse for other orders unless the inventory reservation, or part of the inventory reservation, is canceled.

There are several reasons for reserving inventory:

- First ordered, first delivered, which means that customers get available items in the same order in which they place their orders.
- Shortage of items due to a long or unknown delivery time from the vendor. You might want to make sure that certain customers or orders get delivery of the first-available items.
- Certain customers and certain types of orders have first priority for delivery.
- Items with serial or batch numbers. You can mark certain items that have been or will be delivered to specific orders.
- Specially ordered items that are reserved for certain orders.
- Production orders. For example, you can mark items that are produced for and adjusted to specific orders.

Inventory can be reserved automatically when a new order line is created, or inventory can be reserved manually on the individual orders. It's also possible to reserve inventory at different stages in a production process. Only stocked products can be reserved. Services can't be reserved, because there's no on-hand inventory. Both physical on-hand inventory and ordered, but not yet received, inventory can be reserved. If a larger quantity is reserved than what the on-hand inventory contains, a message displays that you can't reserve such a large quantity. You can then either reserve the quantity anyway, or change the ordered quantity. The quantity can be either reserved or changed. If more items are reserved than are available, the shortage is covered the next time that items are available for delivery.

## Inventory reservation policies

Inventory reservation policies are set on the **Item model groups** page, the **Inventory and warehouse management parameters** page, and the **Production parameters** page.

### Policies on the Item model groups page

The **Inventory policies** section contains the following reservation policies.

| Reservation policy | Description |
|---|---|
| FIFO date-controlled | If you select the **FIFO date-controlled** option, the inventory reservation is controlled by a sorting date according to the FIFO principle. Batches are reserved based on the earliest date of receipt of items, according to the principle of first in, first out (FIFO). |
| Backward from ship date | This option becomes available if you've selected the **FIFO date-controlled** option. If you select **Backward from ship date**, and if you're reserving available physical inventory, then the inventory reservation is controlled by the last update physical date according to the FIFO rule. If you're reserving available ordered inventory, the inventory is reserved backward from the desired ship date according to the principle of last in, first out (LIFO). If no receipts are available before the ship date, the reservation will follow the LIFO rule using the transaction ship date. |
| Item sales reservation | Determines whether item reservation is manual or automatic. If a reservation is automatic, inventory is reserved when order lines are created. It’s possible to make reservations at the item number level for BOMs (**Automatic** option), or for the individual elements of a BOM (**Explosion** option). The default value for **Item sales reservation** may be inherited from **Accounts receivable parameters.** On that page, the value is set in the Reservation field in the **Sales default values** **section** on the **General** tab. |
| Same batch selection | Same batch reservation lets you reserve inventory for a sales order line against a single batch of inventory. If you want to use this option, you must also set the **Consolidate requirement** option to **Yes**. There are additional settings that are required for the tracking dimension group and storage dimension group. For more information, see [Reserve the same batch for a sales order](../sales-marketing/reserve-same-batch-sales-order.md). |
| Consolidate requirement | This option is similar to the **Same batch selection** option, and it consolidates inventory that’s reserved for sales order lines into a single requirement. |
| FEFO date-controlled | This option allows you to reserve batches that are close to their expiration date or best before date. You also need to set the **Pick criteria** field to select either **Expiration date** or **Best before date**. |

#### Example for FIFO date-controlled and Backward from ship date

In this example, on-hand inventory for item number A exists for three different batch numbers.

| Item number | Batch number | Quantity | Date |
|---|---|---|---|
| A | 1000 | 5 | February 2, 2016 |
| A | 1001 | 3 | January 1, 2016 |
| A | 1002 | 7 | March 3, 2016 |

A sales order that should be automatically reserved and delivered on April 4, 2016, reserves the following batch:

- If both the **FIFO date-controlled** and **Backward from ship date** check boxes are cleared, batch 1000 is reserved because it's the batch with the lowest number.
- If the **FIFO date-controlled** check box is selected and the **Backward from ship date** check box is cleared, batch 1001 is reserved because it's the batch with the first date of receipt (FIFO).
- If both the **FIFO date-controlled** and **Backward from ship date** check boxes are selected, batch 1002 is reserved because it's the batch receipt closest to the sales order ship date.

### Policies on the Inventory and warehouse management parameter page

There are two options related to reservations on the **Inventory and warehouse management parameters** page:

- The **Reserve ordered items** option on the **General** tab lets you reserve item receipts that are ordered against item issues in Accounts receivable, Project management and accounting, and Production control. If you clear this option, you can only reserve items that have been physically received. If a particular item has been set up to accept negative inventory, this field isn't relevant.
- The **Reserve items automatically** option on the **Transfer** tab determines the default setting if items are automatically reserved for transfer orders. The default setting can be overridden on individual transfer orders.

### Inventory reservation policies on the Production parameters page

The value of the **Reservation** field on the **General** tab on the **Production parameters** page determines the default point in the production process at which inventory should be reserved. For example, inventory could be reserved when work is scheduled, or when work is started.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
