---
title: Link transfer order lines with sales order lines (preview)
description: Learn how to link transfer order lines to the sales order lines from which they were created. You can also add new transfer order lines to open transfer orders provided they are for the same warehouses.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form: SalesTable, InventTransferOrderSalesLineSupplyForm, InventTransferOrders, InventTrans
ms.topic: how-to
ms.date: 07/31/2024
ms.custom: 
  - bap-template
---

# Link transfer order lines with sales order lines (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!--KFM: Preview until further notice. -->

Dynamics 365 Supply Chain Management lets you create transfer order lines directly from sales order lines, which is useful when the goods you need to supply are located in another warehouse than the one you're shipping from. The feature described in this article expands on this functionality by linking and marking the related transfer and sales order lines together. This makes it easier to track the relationship between the sales and transfer orders and helps you manage your inventory more effectively. The feature adds the following capabilities and benefits:

- View all transfer orders generated for a specific sales order line.
- View all sales orders related to a specific transfer order line.
- Choose to add transfer lines to either an existing or newly created transfer order when creating them from a sales order.
- Avoid creating multiple transfer orders for the same sales order line. The system shows a warning if you try to do this action.
- Automatically reserve transfer order quantities for the sales order from which they were created, thereby preventing them from being used to fulfill another sales order by mistake. (The inventory transaction record for the sales order line is automatically set with an **Issue** status of *Reserved ordered*, which means that when the transferred stock is received, it's immediately reserved against the sales order.)
- Automatically mark new transfer order lines with their related sales order lines. Marking matches specific inventory receipts (transfer order line inventory transactions) with inventory issues (sales order line inventory transactions) for the purpose of inventory costing.  <!--KFM: Please confirm this -->

<!--KFM: Maybe add a bullet to describe what the **Reserve items automatically** function does. -->

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *(Preview) Pair transfer order lines with sales order lines* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Add and link lines to a new or existing transfer order from a sales order

To create transfer order lines directly from sales order lines, link the lines together, and (optionally) reserve the transferred inventory, follow these steps:

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order for which you want to add lines to a transfer order.
1. On the **Sales order lines** FastTab, select the lines that you want to add to the transfer order.
1. From the **Sales order lines** FastTab toolbar, select **Product and supply** \> **New** \> **Transfer order**.
1. The **Transfer order** dialog opens. Make the following settings:
    - **From warehouse** - Select warehouse from which the items should be transferred.
    - **To warehouse** - Select warehouse to which the items should be transferred. This is the warehouse associated with the sales order line and should already be selected.
    - **Add to an existing transfer order** - If you want to add the items to an existing transfer order, select the transfer order from the list. The list only shows open transfer orders that use the **From warehouse** and **To warehouse** selected in this dialog. If you want to create a new transfer order, leave this field blank.
    - **Ship date** - The date on which the items should be shipped.
    - **Reserve items automatically** - If you want the items to be reserved automatically for the sales order that created the transfer order line, set this option to *Yes*. <!--KFM: Are we reserving the stock for the sales order (in the To warehouse) or for the transfer order (in the From warehouse), or both? -->

1. Select **OK**.
1. The new or selected transfer order opens. You can now view the transfer order lines and other details.

## View transfer order lines related to a sales order

When you're reviewing sales orders, you can confirm whether the required transfer order lines exist for each sales order line. To do so, follow these steps:

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to check.
1. From the **Sales order lines** FastTab toolbar, select **Product and supply** \> **View** \> **Related transfer orders**.
1. The **Paired transfer order and sales order lines** page opens. It lists the following information about all transfer order lines that are linked to the sales order you selected:
    - **Item number** – The item number of product in the sales order line and transfer order line. Select this link to see the item details.
    - **Sales order** – The identifier of the sales order. Select this link to open the sales order.
    - **Line number** – Line number of the sales line.
    - **Sales quantity** – Sales quantity of the sales line.
    - **Transfer number** – The identifier of the transfer order. Select this link to open the transfer order.
    - **From warehouse** – The source warehouse of the transfer order.
    - **To warehouse** – The destination warehouse of the transfer order. This is also the warehouse for the related sales order line.
    - **Line number** – Line number of the transfer order line.
    - **Transfer quantity** – Transfer quantity of the transfer order line.
    - **Ship date** – Ship date of the transfer order line.
    - **Receive date** – Receipt date of the transfer order line.
    - **Remaining** – Remaining status of the transfer order line (possible values include: *Nothing*, *Receive updates*, and *Shipping updates*).

    From this page, you can also see more information about a selected line by selecting one of the following actions from the Action Pane:

    - **Sales order line transactions** – View all inventory transactions related to the sales order line.
    - **Transfer order line transactions** – View all inventory transactions related to the transfer order line.

## View sales orders related to a transfer order line

When you're reviewing transfer orders, you can check to see whether they contain lines that are related to a specific sales order. This process can help you understand the context of the transfer order and why it was created. To do so, follow these steps:

1. Go to one of the following pages:
    - **Inventory management** \> **Inbound orders** \> **Transfer order**.
    - **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Open the transfer order that you want to check.
1. On the **Transfer order lines** FastTab, select the line you want to view the related sales order for.
1. From the **Transfer order lines** FastTab toolbar, select **Inventory** \> **Related sales order**.
1. The **Paired transfer order and sales order lines** page opens. It lists information about the sales order line that's related to the transfer order line you selected. The columns and Action Pane commands are the same as those described in the previous section.

## Automatic marking between sales and transfer order lines

*Marking* matches specific inventory receipts (transfer order line inventory transactions) with inventory issues (sales order line inventory transactions) for the purpose of inventory costing <!--KFM: Is it right that this is about costing? Is at also about reserving the transferred inventory for fulfilling the matching sales order? Is it also about preventing multiple transfers for the same sales order line? -->. When you create a transfer order line from a sales order line, the system automatically marks the two lines together if possible.

> [!IMPORTANT]
> Automatic marking is only supported for *non-settled items*, which are items from transactions that haven't been matched or processed according to the inventory model you are using (such as standard cost, moving average, or non-valuated). Catch-weight items are likewise not supported for automatic marking. In theses cases you must do the marking manually.

To view and edit markings from a sale order line, follow these steps:

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to check.
1. On the **Sales order lines** FastTab, select the line you want to view the marking for.
1. On the **Sales order lines** FastTab toolbar, select **Inventory** \> **Maintain** \> **Marking**.
1. The **Marking** dialog opens, showing the marked quantities. You can edit the markings if needed.

To view and edit markings for a specific inventory transaction, follow these steps:

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to check.
1. On the **Sales order lines** FastTab, select the line you want to view transactions for.
1. On the **Sales order lines** FastTab toolbar, select **Inventory** \> **View** \> **Transactions**.
1. The **Inventory transactions** page opens. Select the transaction you want to inspect. You can inspect both shipment and receipt transactions.
1. On the Action Pane, open the **Inventory** tab and, from the **View** group, select **Marking**.
1. The **Marking** dialog opens, showing the marked quantities. You can edit the markings if needed.

To view and edit markings from a transfer order line, follow these steps:

1. Go to one of the following pages:
    - **Inventory management** \> **Inbound orders** \> **Transfer order**.
    - **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Open the transfer order that you want to check.
1. On the **Transfer order lines** FastTab, select the line you want to view the related sales order for.
1. From the **Transfer order lines** FastTab toolbar, select **Inventory** \> **Transactions**.
1. The **Inventory transactions** page opens. Select the transaction you want to inspect.
1. On the Action Pane, open the **Inventory** tab and, from the **View** group, select **Marking**.
1. The **Marking** dialog opens, showing the marked quantities. You can edit the markings if needed.
