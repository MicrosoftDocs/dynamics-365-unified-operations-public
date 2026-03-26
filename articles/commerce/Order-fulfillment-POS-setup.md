---
title: Set up order fulfillment for stores
description: Learn how to set up store order fulfillment in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 01/27/2026
ms.topic: how-to
ms.search.form:  RetailStoreTable, RetailTillLayout
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2017-10-30
ms.custom: 
  - bap-template
---

# Set up order fulfillment for stores

[!include [banner](includes/banner.md)]

This article describes how to set up store order fulfillment in Microsoft Dynamics 365 Commerce.

Many retailers want to optimize order fulfillment by enabling stores to fill orders. Order fulfillment at the store level can help mitigate overstock scenarios for a specific store, or it might be needed in cases where a store has extra capacity or is located within a closer shipping distance to the customer. To address this need, a unified order fulfillment operation is available at the point of sale (POS).

Orders for fulfillment at a specific store have the store's warehouse designated on the header or lines of the order.

The order fulfillment operation at the POS provides a single work area where cashiers can perform order processing operations such as accepting orders, marking orders as shipped, and initiating store pickup.

## Set up the order fulfillment operation

Use the order fulfillment operation (Operation ID 928 on [Online and offline point of sale (POS) operations](pos-operations.md)) to access the store order fulfillment work area in the POS.

To specify which parameter to use when invoking order fulfillment from the POS, see [Add the operation to a button grid](pos-screen-layouts.md#button-grid-designer). By default, after specifying the order fulfillment operation, the **All orders** parameter is selected. Assign the following parameters to POS buttons to give users various ways to view order fulfillment.

- **All orders** parameter - When you configure the operation with this parameter, it lists all order lines for fulfillment at the current store.
- **Orders to ship** parameter - When you assign this parameter to a button, it lists only orders that ship out of the store.
- **Orders for pick up** parameter - When you assign this parameter to a button, it lists only orders to be picked up at the store.

### Enable users to access order fulfillment from the POS

The order fulfillment operation doesn't have its own permission out-of-the-box, but in the future, users might require the **Allow retrieve order** permission to invoke the operation from the POS.

At the store level, a configuration setting determines whether an order line must be accepted manually from within the POS. If you don't set that configuration option, order lines are accepted by default. If you turn on that configuration option, POS users must have the **Allow accept order** permission to accept orders from within the POS.

### Enable manual order acceptance

Order lines assigned to a store are marked as **Accepted** by default because the system assumes the assigned store fulfills the order and that the order isn't subject to reassignment. In certain cases, retailers might want to manually accept orders before they can be fulfilled. For example, if a store is short staffed and can't fulfill orders, a store manager accepts only as many orders for processing as they feel can be adequately processed in a given day. Until an order is accepted, headquarters can reassign it to a different store. Order acceptance also provides a way to indicate that a store acknowledges an order and will fulfill it.

Order lines for store pickup are marked as **Pending** and aren't subject to acceptance.

To turn on manual acceptance for order lines, go to **Retail and Commerce \> Channels \> Stores \> All stores**. Select the store, select the store ID to view the store's details, and then select **Edit**. On the **General** FastTab, locate the **Order fulfillment** subheader and change the **Manual accept** setting to **Yes**.

### Enable reject order line capability

Workers can also reject order lines from the POS. Rejecting an order line signifies that the store won't fulfill the order and sends the order line back for reassignment to another store or warehouse. The **Allow reject order** permission in the POS permission group associated with the worker grants order line rejection permission. When retailers reject a line, they can require that workers provide a reason for rejection by using info codes of **Info code activity** type **Order fulfillment** and assigning the info code to **Reject order line** in the functionality profile associated with the channel. If you want to conduct further analysis on the rejection reasons, the info code is saved in the INFOCODEID, SUBINFOCODEID, and INFORMATION columns of the RetailSalesLine entity.

> [!NOTE]
> Only the info codes of **Info code activity** type **Order fulfillment** can be assigned to the **Reject order line** action.

### Synchronize changes to the channel database

After you assign the operation to a button grid, assign the proper permissions, and configure the channel, synchronize the changes to the channel database. To do so, go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**. Select schedule "1090-Registers" to sync button grid changes and then select **Run now**. Next, sync permissions changes by selecting "1060-Staff" and then select **Run now**. Next, sync channel changes by selecting "1070-Channel configuration" and select **Run now**. Finally, sync the newly created info code for reject reason by selecting the "1110-Global configuration" and select **Run now**.

## Use order fulfillment from the POS

Open the POS and select the order fulfillment operation. Depending on how it's configured, either all lines, order lines for pickup, or order lines to ship are listed.

### Order fulfillment view

The order fulfillment view lists order lines for fulfillment at the store and includes the following columns:

- Order number
- Product number
- Description
- Quantity ordered
- Requested delivery date
- Customer name
- Fulfillment status

You can view additional information for a specific order line by selecting the order line and then opening the flyout menu located just below the signed-in user/shift information shown in the POS header. This menu includes two tabs: one for line details and another for order details. The line details tab includes the following information:

- Quantity ordered
- Quantity remaining to be shipped or picked up
- Quantity picked
- Quantity packed
- Quantity invoiced (already picked up or shipped)
- Mode of delivery
- Delivery address

The details flyout menu also has a tab that provides more order level details including:

- Customer name
- Customer ID
- Order number
- Order total
- Order balance

The action pane at the bottom of the order fulfillment view contains all of the actions that you can take against an order line. If an action isn't available based on a line's status, that action is unavailable.

By default, orders have a status of **Accepted**. You can view order status as a column in the list of order lines. If you configure **Manual accept** at the channel level, all lines to ship show as **Pending** and must be accepted before they can be fulfilled. Orders for store pickup are **Pending** by default and don't need to be accepted.

### Order fulfillment line actions

- **Edit** – If an order status is pending, you can edit it from the POS. You can't edit orders that are already partially picked, packed, or invoiced from the order fulfillment view.
- **Accept** – If you configure **Manual accept** at the channel level, you must first accept lines before they can move through the order fulfillment process.
- **Pick** – The pick option supports several actions:
    - The **Picking** action updates the status of the order line so other store employees don't attempt to pick the same line.
    - The **Print picking list** action prints a picking list for the selected line or lines and also updates their status to **Picking**. Picking list formats are controlled as part of receipt formats. For more information about how to set up receipt formats, see [Receipt templates and printing](receipt-templates-printing.md).
    - The **Mark as picked** action indicates that the line is picked. **Mark as picked** initiates corresponding inventory transactions in headquarters. Picking actions can be performed at the same time for multiple order lines across orders and for all modes of delivery.
- **Reject** – You can reject lines or partial lines, which allows headquarters to reassign them to another store or warehouse. You can only reject lines if they aren't yet picked or packed. To reject a line that is already picked or packed, headquarters must unpick or unpack that line.
- **Pack** – The pack option supports two actions: **Print packing slip** prints a packing slip for the selected lines, and **Mark as packed** marks the lines as packed and delivered in headquarters. You can only pack order lines that belong to the same order and have the same mode of delivery. Packing slip formats are controlled as part of receipt formats. For more information about how to set up receipt formats, see [Receipt templates and printing](receipt-templates-printing.md).
- **Ship** – The ship action marks selected lines as **Delivered** in headquarters. After a line is fully shipped, it no longer appears in the order fulfillment view.
- **Pickup** – The pickup action adds the lines to the transaction view for pickup. If there are other lines on the order that aren't being picked up, the process adds them to the transaction view with a quantity of zero. After a line is fully picked up, it no longer appears in the order fulfillment view.

### Order fulfillment filtering

Order fulfillment at the POS includes filtering to help the user easily find what they need. Change filters on the action pane at the bottom of the **Point of sale** screen. By default, a **Delivery type** filter is applied, based on how the operation is set up. If the operation is set up with the parameter **All orders**, that filter is applied when accessing order fulfillment. The same filter application applies for the **Store pickup** and **Ship from store** parameters. Other filters that you can apply to the order fulfillment view include:

- Customer number
- Customer name
- Customer email
- Order number
- Mode of delivery
- Receipt number
- Channel Reference ID
- Originating store number
- Line status
- Created date
- Delivery date
- Receipt date


[!INCLUDE[footer-include](../includes/footer-banner.md)]
