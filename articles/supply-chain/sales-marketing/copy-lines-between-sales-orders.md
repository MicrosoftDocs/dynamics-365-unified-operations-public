---
title: Copy lines between sales orders
description: Learn how to copy lines between sales orders, which can save time when creating new orders that are similar to existing orders.
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

The *copy from all* feature lets you copy sales order lines between sales orders. This feature is useful when you need to create order that is similar to an existing one.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Either [create a new sales order](tasks/create-sales-orders.md) or open an existing sales order to which you want to copy lines.
1. On the Action Pane, open the **Sales order** tab and then, from the **Copy** group, select **From all**.
1. On the **Copy from all** dialog, expand the **Parameters** FastTab and make the following settings.
    - **Quantity factor** – Specify the factor that quantity for the selected order lines is to be increased or decreased by.
    - **Invert sign** – Choose whether to create inverted (negative) quantities for the copied lines. Set this option to *Yes* to create a return order or a negative-quantity order by reversing the sign of the copied lines.
    - **Copy charges** – Choose whether to copy order line charges. If **Copy order header** option is also set to *Yes*, then order header charges will also be copied. Set this option to *Yes* to include any additional charges from the original order lines and/or header.
    - **Recalculate price** – Choose whether the net amount of the copied lines should be recalculated based on current prices and trade agreements. Set this option to *Yes* to recalculate the prices.
    - **Copy precisely** – Choose whether the copied lines should be exact copies of the selected lines, including all order information such as sales tax, ledger accounts, and dimensions. Set this option to *Yes* to retain all the original details without any modifications.
    - **Delete order lines** – Choose whether previously entered order lines for the current order should be deleted before copying the new lines. Set this option to *Yes* to replace the existing order lines with the copied lines.
    - **Copy order header** – Choose whether to copy information from the selected order header to the current order. Set this option to *Yes* to copy order header information such as customer details, delivery terms, and payment terms with the selected order.

1. Expand the **Sales orders** FastTab and choose which order lines (possibly header information) you want to copy.
    - In the **Headers** grid, find and select the sales order that you want to copy lines from. You can only copy from one order at a time.
    - In the **Lines** grid, select the checkbox for each line that you want to copy. To select all the lines at once, select the checkbox in **Select all** column for your selected order in the **Header** grid.

    > [!NOTE]
    > You can copy other related records and fields in a similar way using the other FastTabs on the page.

1. Select **OK** to close the dialog.
1. Your selected sales order lines (and possibly header information) are now copied to the current order.
