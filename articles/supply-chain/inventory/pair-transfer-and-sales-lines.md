---
title: Link transfer order lines with sales order lines (preview)
description: Learn how to link transfer order lines to the sales order lines that they were created from. You can also add new transfer order lines to open transfer orders if they are for the same warehouses.
author: Weijiesa
ms.author: weijiesa
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

Microsoft Dynamics 365 Supply Chain Management lets you create transfer order lines directly from sales order lines. This functionality is useful when the goods that you must supply are located in a different warehouse than the warehouse that you're shipping from.

The feature that is described in this article expands on that functionality by linking and marking the related transfer and sales order lines together. This link makes it easier to track the relationship between the sales and transfer orders, and helps you manage your inventory more effectively. The feature adds the following capabilities and benefits:

- View all transfer orders that were generated for a specific sales order line.
- View all sales orders that are related to a specific transfer order line.
- When transfer lines are created from a sales order, you can choose to add them either to an existing transfer order or to a newly created transfer order.
- You receive a warning if you try to create multiple transfer orders for the same sales order line.
- Automatically mark new transfer order lines with their related sales order line. Marking matches specific inventory receipts (transfer order line inventory transactions) with inventory issues (sales order line inventory transactions) for the purpose of inventory costing.
- Automatically reserve transfer order quantities for the sales order that they were created from. In this way, you prevent them from being used to fulfill another sales order by mistake.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use the feature that is described in this article, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *(Preview) Pair transfer order lines with sales order lines* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Add and link lines to a new or existing transfer order from a sales order

To create transfer order lines directly from sales order lines, link the lines together, and (optionally) reserve the transferred inventory, follow these steps.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order for which you want to add lines to a transfer order.
1. On the **Sales order lines** FastTab, select the lines that you want to add to the transfer order.
1. On the toolbar of the **Sales order lines** FastTab, select **Product and supply** \> **New** \> **Transfer order**.
1. In the **Transfer order** dialog box, set the following fields:

    - **From warehouse** – Select the warehouse that the items should be transferred from (source warehouse).
    - **To warehouse** – Select the warehouse that the items should be transferred to (destination warehouse). This warehouse is the one that is associated with the sales order line. It should be selected by default.
    - **Add to an existing transfer order** – If you want to add the items to an existing transfer order, select the transfer order in the list. The list shows only open transfer orders that use the source and destination warehouses that are selected in this dialog box. If you want to create a new transfer order, leave this field blank.
    - **Ship date** – The date when the items should be shipped.
    - **Reserve items automatically** – If you want the items in the source warehouse to be reserved automatically for the transfer order, set this option to *Yes*.

1. Select **OK**.

The new or selected transfer order is opened. You can now view the transfer order lines and other details.

## View transfer order lines related to a sales order

When you review sales orders, you can confirm whether the required transfer order lines exist for each sales order line.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to review.
1. On the **Sales order lines** FastTab, on the toolbar, select **Product and supply** \> **View** \> **Related transfer orders**.
1. On the **Paired transfer order and sales order lines** page, you can review the following information about all the transfer order lines that are linked to the selected sales order:

    - **Item number** – The item number of product on the sales order line and the transfer order line. Select the link to view the item details.
    - **Sales order** – The identifier of the sales order. Select the link to open the sales order.
    - **Line number** – The line number of the sales order line.
    - **Sales quantity** – The sales quantity of the sales order line.
    - **Transfer number** – The identifier of the transfer order. Select the link to open the transfer order.
    - **From warehouse** – The source warehouse of the transfer order.
    - **To warehouse** – The destination warehouse of the transfer order. This warehouse is also the warehouse for the related sales order line.
    - **Line number** – The line number of the transfer order line.
    - **Transfer quantity** – The transfer quantity of the transfer order line.
    - **Ship date** – The ship date of the transfer order line.
    - **Receive date** – The receipt date of the transfer order line.
    - **Remaining** – The remaining status of the transfer order line. Possible values include *Nothing*, *Receive updates*, and *Shipping updates*.

1. To view more information about a selected line, select one of the following buttons on the Action Pane:

    - **Sales order line transactions** – View all inventory transactions that are related to the sales order line.
    - **Transfer order line transactions** – View all inventory transactions that are related to the transfer order line.

## View sales orders related to a transfer order line

When you review transfer orders, you can check whether they contain lines that are related to a specific sales order. This process can help you understand the context of the transfer order and why it was created.

1. Follow one of these steps:

    - Go to **Inventory management** \> **Inbound orders** \> **Transfer order**.
    - Go to **Inventory management** \> **Outbound orders** \> **Transfer order**.

1. Open the transfer order that you want to review.
1. On the **Transfer order lines** FastTab, select the line that you want to view the related sales order for.
1. On the toolbar of the **Transfer order lines** FastTab, select **Inventory** \> **Related sales order**.
1. On the **Paired transfer order and sales order lines** page, you can review information about the sales order line that is related to the selected transfer order line. The grid columns and Action Pane buttons are the same as the ones that are described in the previous section.

## Automatic marking between sales and transfer order lines

Marking matches specific inventory receipts (transfer order line inventory transactions) with inventory issues (sales order line inventory transactions) for the purpose of inventory costing. When you create a transfer order line from a sales order line, the system automatically marks the two lines together, but only if they are for *nonsettled items*.

> [!IMPORTANT]
> Nonsettled items are items from transactions that haven't been matched or processed according to the inventory model that you're using. (Examples of inventory models include standard cost, moving average, and non-valuated.) Automatic marking isn't supported for settled items. It also isn't supported for catch-weight items. For settled and catch-weight items, you must do the marking manually.

To view and edit markings from a sale order line, follow these steps.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to review.
1. On the **Sales order lines** FastTab, select the line that you want to view the marking for.
1. On the toolbar of the **Sales order lines** FastTab, select **Inventory** \> **Maintain** \> **Marking**.
1. The **Marking** dialog box shows the marked quantities. You can edit the markings as required.

To view and edit markings for a specific inventory transaction, follow these steps.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to review.
1. On the **Sales order lines** FastTab, select the line that you want to view transactions for.
1. On the toolbar of the **Sales order lines** FastTab, select **Inventory** \> **View** \> **Transactions**.
1. On the **Inventory transactions** page, select the transaction that you want to inspect. You can inspect both shipment transactions and receipt transactions.
1. On the Action Pane, on the **Inventory** tab, in the **View** group, select **Marking**.
1. The **Marking** dialog box shows the marked quantities. You can edit the markings as required.

To view and edit markings from a transfer order line, follow these steps.

1. Follow one of these steps:

    - Go to **Inventory management** \> **Inbound orders** \> **Transfer order**.
    - Go to **Inventory management** \> **Outbound orders** \> **Transfer order**.

1. Open the transfer order that you want to review.
1. On the **Transfer order lines** FastTab, select the line that you want to view the related sales order for.
1. On the toolbar of the **Transfer order lines** FastTab, select **Inventory** \> **Transactions**.
1. On the **Inventory transactions** page, select the transaction that you want to inspect.
1. On the Action Pane, on the **Inventory** tab, in the **View** group, select **Marking**.
1. The **Marking** dialog box shows the marked quantities. You can edit the markings as required.

## Automatically reserve transferred items for their matching sales orders

Transfer order quantities can be automatically reserved for the sales order that they were created from. In this way, they can't be used to fulfill another sales order by mistake. For this functionality to work, the following conditions must be met:

- The **Reserve items automatically** option must be set to *Yes* when the transfer order line is created from the sales order line.
- The inventory transactions for the related sales order line and transfer order line must be marked together automatically. (Automatic marking is supported only for nonsettled items.)

If the preceding conditions are met, the transferred stock is automatically reserved against the sales order line when it's received. In this case, the inventory transaction record that is created for the sales order line has an issue status of *Reserved ordered*, and the reservation is triggered.

If the conditions aren't met, the transferred stock isn't automatically reserved against the sales order line. In this case, the inventory transaction record that is created for the sales order line has an issue status of *On order*.
