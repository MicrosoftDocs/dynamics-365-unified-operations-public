---
title: Create a sales order using copy from all
description: Learn how to copy lines from one sales order to another, which can save time when creating new orders that are similar to existing orders.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCopying, SalesTable
ms.topic: how-to
ms.date: 03/19/2025
ms.custom: 
  - bap-template
---

# Create a sales order using copy from all

[!include [banner](../../includes/banner.md)]

The *copy from all* feature lets you create a new sales order that starts as a copy of an existing order. The new copy includes all the lines from the original order, and you can modify the new order as needed. This feature is useful when you need to create a new order that is similar to an existing one.

<!-- KFM: I don't think we can create a new order based on a copy, just copy lines from an existing order into a selected order. Is that right? If so, we should change the title and intro to reflect this. -->

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Either [create a new sales order](create-sales-orders.md) or open an existing sales order to which you want to copy lines. <!-- KFM: This seems to be necessary. Right? -->
1. On the Action Pane, open the **Sales order** tab and then, from the **Copy** group, select **From all**.
1. On the **Copy from all** dialog, expand the **Parameters** FastTab and make the following settings.
    - **Reason code** – <!-- KFM: description needed -->
    - **Reason comment** – <!-- KFM: description needed -->
    - **Quantity factor** – <!-- KFM: description needed -->
    - **Invert sign** – Choose whether to create inverted (negative) quantities for the copied lines. Set this option to *Yes* to create a return order or a negative-quantity order by reversing the sign of the copied lines.
    - **Copy charges** – Choose whether to copy order line charges. If **Copy order header** option is also set to *Yes*, then order header charges will also be copied. Set this option to *Yes* to include any additional charges from the original order lines and/or header.
    - **Recalculate price** – Choose whether the net amount of the copied lines should be recalculated based on current prices and trade agreements. Set this option to *Yes* to recalculate the prices.
    - **Copy precisely** – Choose whether the copied lines should be exact copies of the selected lines, including all order information such as GST <!-- KFM: spell out "GST" -->, ledger accounts, and dimensions. Set this option to *Yes* to retain all the original details without any modifications.
    - **Delete order lines** – Choose whether previously entered order lines for the current order should be deleted before copying the new lines. Set this option to *Yes* to replace the existing order lines with the copied lines.
    - **Copy order header** – Choose whether information from the selected order header should be copied to the current order. Set this option to *Yes* if you want to include header information such as customer details, delivery terms, and payment terms from the original order. <!-- KFM: This doesn't seem to work. More detail needed? Overwrites existing header information or not? -->

1. Expand the **Sales orders** FastTab and choose which order lines (possibly header information) you want to copy.
    - In the **Headers** grid, find and select the sales order that you want to copy lines from. You can only copy from one order at a time.
    - In the **Lines** grid, select the checkbox for each line that you want to copy. To select all the lines at once, select the checkbox in **Select all** column for your selected order in the **Header** grid.

    <!-- KFM: there are many more FastTabs here (Quotations, Confirmation, Packing slips, etc.). What can use them for? We should mention them and provide a summary of what each could be used for (or tell the user not to use them) -->

1. Select **OK** to close the dialog.
1. Your selected sales order lines (and possibly header information) is now copied to the current order.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
