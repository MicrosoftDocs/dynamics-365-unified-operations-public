---
title: Register the receipt of returned items
description: Learn how you can register the receipt of returned items using the Arrival overview page or the Registration page, including a step-by-step process.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/01/2018
ms.custom: 
ms.reviewer: kamaybac
ms.search.region: Global 
ms.search.form: WMSArrivalOverview, InventTransRegister
---

# Register the receipt of returned items

[!include [banner](../includes/banner.md)]

There are two methods for registering the receipt of returned items. The first method is a warehouse receiving process that uses the **Arrival overview** page. The second uses the **Registration** page.

## Register the receipt of returned items in the Arrival overview page

You can use the **Arrival overview** page to identify a return shipment by its Return Material Authorization (RMA) number. If a journal name is defined on the **Setup** tab, and journal lines that correspond to the lines selected on the **Arrival overview** page exist, a new journal header is created when you select **Start arrival**.

1. Go to **Inventory management** \> **Periodic** \> **Arrival overview**.

1. In the **Setup name** field, select **Return order**, and then select **Update**.

    > [!TIP]
    > You can use the **Range** fields to narrow the search results. You can type or select the RMA number in the **RMA number** field for an exact result. To define and save a set of filters that will restrict which incoming arrivals are displayed, select the **Setup** tab. The available filters include types, warehouses, and docks.

    > [!WARNING]
    > Return orders cannot be mixed with other arrival types in the **Arrival overview** page. Therefore, the reference will always be sales order, but no sales order ID will be specified on the journal header.

1. In the **Receipts** grid, locate the line that matches the item being returned, and then select the check box in the **Select for arrival** column.

1. To exclude certain lines from the return receipt, such as items from the original order that were not included in the return shipment, clear the associated **Select for arrival** check boxes in the **Lines** table in the lower part of the page.

1. Select the **Start arrival** button to create an arrival journal.

    > [!NOTE]
    > You can select multiple return orders and include them all in a single arrival process. Each return order line will be copied into a corresponding item arrival journal line.

    > [!NOTE]
    > You can also manually create an arrival journal by using the **Item arrival** page.

1. Go to **Inventory management** \> **Journals** \> **Item arrival** \> **Item arrival**.

1. Select the arrival journal that you just created and then select **Lines** to open the **Journal lines, locations** page.

1. On the **General** tab, adjust the number in the **Quantity** field, if it is required, and then assign a disposition code in the **Disposition code** field.

    Alternatively, you can select the **Quarantine management** check box to have the returned items sent through an inspection process in the context of a quarantine order.

    > [!NOTE]
    > If you send the returned items through quarantine, you cannot specify a disposition code.

1. Select the **Validate** button.

1. If there are no errors in the validation process, select **Post**.

## Register the receipt of returned items in the Registration page

As an alternative to using the **Arrival overview** page, you can use the **Registration** page to register the arrival of returned items.

1. Go to **Sales and marketing** \> **Sales returns** \> **All return orders**. Create a new return order or open the return order from the list. On the **Lines** FastTab, select the return order line. Select **Update line**, and then select **Registration**.

1. Assign a disposition code in the **Disposition code** field, and then select **OK**.

    > [!NOTE]
    > It is not possible to send the item for inspection as a quarantine order using the **Registration** page.

1. In the **Transactions** grid, select the transaction to be registered.

1. In the **Register now** grid, select **Add**. Repeat the previous two steps until all of the returned items appear in the **Register now** grid.

1. Select **Post all**.

## Related information

- [Arrival overview (form)](https://technet.microsoft.com/library/hh227654\(v=ax.60\))

[!INCLUDE[footer-include](../../includes/footer-banner.md)]