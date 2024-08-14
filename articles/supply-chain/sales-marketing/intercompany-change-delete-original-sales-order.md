---
title: Change or delete an original intercompany sales order
description: Learn about changing and deleting an original sales order functionality, including a table that defines results for various operations.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable
---

# Change or delete an original intercompany sales order

[!include [banner](../../includes/banner.md)]

When you change a sales order, your changes are automatically synchronized with both the relevant intercompany purchase order and the intercompany sales order.

> [!NOTE]
> Purchase orders for external vendors are not affected by any changes that you make; neither are the original sales lines that are connected to purchase-order lines for external vendors.

The following table summarizes the changes you can make and the expected results.

| Operation | Result |
|---|---|
| Delete&nbsp;an&nbsp;original&nbsp;sales&nbsp;order. | The related intercompany purchase order and the intercompany sales order are also deleted. If the status of the order is **Picking list** or later in the process, you cannot delete the sales order. |
| Delete an original sales-order line. | The related intercompany purchase order line and the intercompany sales order line are deleted. If the status of the order is **Picking list** or later in the process, you cannot delete the sales order line. |
| Add a new sales line to an original sales order. | The new sales line is created on both the intercompany purchase order and the intercompany sales order. |
| Change the quantity on an original sales-order line. | The quantity is synchronized with both the intercompany purchase-order line and the intercompany sales-order line. The net amount is recalculated on all the orders. |
| Disable direct delivery on an original sales order. | You cannot change the **Direct delivery** field on the original sales order if the intercompany sales order line has reached a minimum status of **Picking list**, **Output order**, or **Picking list journal**. The delivery address on the intercompany purchase order is changed to the standard delivery address (standard purchase order delivery address). Also, the intercompany purchase order lines are changed to the standard delivery address for the lines. Both are synchronized with the intercompany sales order and the lines. The delivery type on all lines on the original sales order is changed to **None**, and the field is synchronized with the intercompany purchase-order lines. Purchase orders for external vendors are not affected; neither are the original sales lines that are connected to purchase-order lines for external vendors. The delivery date on the intercompany purchase order and lines – and the Requested receipt/shipping dates on the intercompany sales order and lines – are updated. |
| Enable direct delivery on an original sales order. | If the intercompany sales order line has reached a minimum status of **Picking list**, **Output order**, or **Picking list journal**, you cannot change the **Direct delivery** field on the original sales order. The delivery address on the intercompany purchase order is changed to the delivery address from the original sales order and synchronized with the intercompany sales order. The delivery type on all lines on the original sales order is changed to **Direct delivery**, and the field is synchronized with the intercompany purchase-order lines. The delivery address on each original sales-order line is synchronized with both the intercompany purchase-order lines and the intercompany sales-order lines. The delivery date on the intercompany purchase order and lines – and the Requested receipt/shipping dates on the intercompany sales order and lines – are updated. |
| Add a note to both an original sales-order header and the lines. | The note is copied to the intercompany purchase order and the intercompany sales order. |
| Change or delete a note. | If you change or delete a note, the corresponding note on the intercompany purchase order and the intercompany sales order is changed or deleted accordingly. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
