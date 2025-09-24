---
title: Copy lines between sales orders
description: Learn how to copy lines between sales orders. This feature can help save time when you create new orders that are similar to existing orders.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCopying, SalesTable
ms.topic: how-to
ms.date: 03/31/2025
ms.custom: 
  - bap-template
---

# Copy lines between sales orders

[!include [banner](../../includes/banner.md)]

The *copy from all* feature lets you copy sales order lines between sales orders. This feature is useful when you must create an order that is similar to an existing one.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Either [create a new sales order](tasks/create-sales-orders.md) or open an existing sales order that you want to copy lines to.
1. On the Action Pane, on the **Sales order** tab, in the **Copy** group, select **From all**.
1. In the **Copy from all** dialog, on the **Parameters** FastTab, set the following fields:

    - **Quantity factor** – Specify the factor that the quantity for the selected order lines should be increased or decreased by.
    - **Invert sign** – Specify whether inverted (negative) quantities should be created for the copied lines. Set this option to *Yes* to create a return order or a negative-quantity order by reversing the sign of the copied lines.
    - **Copy charges** – Specify whether order line charges should be copied. Set this option to *Yes* to include any additional charges from the original order lines and/or header. If the **Copy order header** option is also set to *Yes*, order header charges are also copied.
    - **Recalculate price** – Specify whether the net amount of the copied lines should be recalculated based on current prices and trade agreements. Set this option to *Yes* to recalculate the prices.
    - **Copy precisely** – Specify whether the copied lines should be exact copies of the selected lines. Exact copies include all order information, such as sales tax, ledger accounts, and dimensions. Set this option to *Yes* to retain all the original details without any modifications.
    - **Delete order lines** – Specify whether previously entered order lines for the current order should be deleted before the new lines are copied. Set this option to *Yes* to replace the existing order lines with the copied lines.
    - **Copy order header** – Specify whether information from the selected order header should be copied to the current order. Set this option to *Yes* to copy order header information together with the selected order. The header information includes customer details, delivery terms, and payment terms.

1. On the **Sales orders** FastTab, specify which order lines (and possibly header information) you want to copy.

    - In the **Headers** grid, find and select the sales order that you want to copy lines from. You can copy from only one order at a time.
    - In the **Lines** grid, select the checkbox for each line that you want to copy. To select all the lines at once, select the checkbox in **Select all** column for the order that you selected in the **Header** grid.

    > [!NOTE]
    > You can use the other FastTabs on the page to copy other related records and fields in a similar way.

1. Select **OK** to close the dialog.

    The selected sales order lines (and possibly header information) are now copied to the current order.
