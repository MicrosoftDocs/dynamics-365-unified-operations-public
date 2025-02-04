---
title: Set up order fulfillment for stores
description: This article describes how to set up store order fulfillment in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 11/29/2023
ms.topic: how-to
ms.search.form:  RetailStoreTable, RetailTillLayout
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2017-10-30
ms.custom: 
  - bap-template
---

# Set up order fulfillment for stores

[!include [banner](includes/banner.md)]

This article describes how to set up store order fulfillment in Microsoft Dynamics 365 Commerce.

Many retailers want to optimize order fulfillment by enabling stores to fill orders. Order fulfillment at the store level can help mitigate overstock scenarios for a specific store, or may be needed in cases where a store has extra capacity, or is located within a closer shipping distance to the customer. To address this need, a unified order fulfillment operation is available at the point of sale (POS).

Orders for fulfillment at a specific store have the store's warehouse designated on the header or lines of the order.

The order fulfillment operation at the POS provides a single work area where cashiers can perform order processing operations such as accepting orders, marking orders as shipped, and initiating store pickup.

## Set up the order fulfillment operation

The order fulfillment operation (Operation ID 928 on [Online and offline point of sale (POS) operations](pos-operations.md)) can be used to access the store order fulfillment work area in the POS.

To specify which parameter to use when invoking order fulfillment from the POS, see [Add the operation to a button grid](pos-screen-layouts.md#button-grid-designer). By default, after specifying the order fulfillment operation, the **All orders** parameter is selected. The following parameters can be assigned to POS buttons to give user various ways to view order fulfillment.

- **All orders** parameter - When configured with this parameter, the order fulfillment operation lists all order lines for fulfillment at the current store.
- **Orders to ship** parameter - When assigned to a button, this parameter only list orders that ship out of the store.
- **Orders for pick up** parameter - When assigned to a button, this parameter only lists orders to be picked up at the store.

### Enable users to access order fulfillment from the POS

The order fulfillment operation doesn't have its own permission out-of-the-box, but in the future, users may require the **Allow retrieve order** permission to invoke the operation from the POS.

At the store level, a configuration setting is available to determines whether an order line must be accepted manually from within the POS. If that configuration option isn't set, order lines are accepted by default. If that configuration option is turned on, POS users must have the **Allow accept order** permission to accept orders from within the POS.

### Enable manual order acceptance

Order lines assigned to a store are marked as **Accepted** by default because it's assumed they'll be fulfilled from the assigned store and aren't subject to reassignment. In certain cases, retailers may want to manually accept orders before they can be fulfilled. For example, if a store is short staffed and is unable to fulfill orders, a store manager only accepts as many orders for processing as they feel can adequately be processed in a given day. Until an order is accepted, headquarters may reassign it to a different store. Order acceptance also provides a way to indicate that an order is acknowledged by a store and will be fulfilled.

Order lines for store pickup are marked as **Pending** and aren't subject to acceptance.

To turn on manual acceptance for order lines, navigate to **Retail and Commerce \> Channels \> Stores \> All stores**. Select the store, select the store ID to view the store's details, and then select **Edit**. On the **General** FastTab, locate the **Order fulfillment** subheader and change the **Manual accept** setting to **Yes**.

### Enable reject order line capability

Order lines can also be rejected from the POS. Rejecting an order line signifies that it won't be fulfilled at that store and sends the order line back for reassignment to another store or warehouse. Order line rejection permission is granted through the **Allow reject order** permission in the POS permission group associated with the worker. When retailers reject a line, they can mandate that workers provide a reason for rejection by using info codes of **Info code activity** type **Order fulfillment** and assigning the info code to **Reject order line** in the functionality profile associated with the channel. If you want to conduct further analysis on the rejection reasons, the info code is saved in the INFOCODEID, SUBINFOCODEID, and INFORMATION columns of the RetailSalesLine entity.

> [!NOTE]
> Only the info codes of **Info code activity** type **Order fulfillment** can be assigned to the **Reject order line** action.

### Synchronize changes to the channel database

After the operation is assigned to a button grid, the proper permissions are assigned, and the channel is configured, the changes must be synchronized to the channel database. To do so, navigate to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**. Select schedule "1090-Registers" to sync button grid changes and then select **Run now**. Next, sync permissions changes by selecting "1060-Staff" and then select **Run now**. Next, sync channel changes by selecting "1070-Channel configuration" and select **Run now**. Finally, sync the newly created info code for reject reason by selecting the "1110-Global configuration" and select **Run now**.

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

Additional information for a specific order line can be viewed by selecting the order line and then opening the flyout menu located just below the signed-in user/shift information shown in the POS header. This menu includes two tabs: one for line details and another for order details. The line details tab includes the following information:

- Quantity ordered
- Quantity remaining to be shipped/picked up
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

The Action Pane at the bottom of the order fulfillment view contains all of the actions that can be taken against an order line. If an action isn't available based on a line's status, that action is unavailable.

By default, orders have a status of **Accepted**. Order status can be viewed as a column in the list of order lines. If **Manual accept** is configured at the channel level, all lines to be shipped show as **Pending** and must be accepted before they can be fulfilled. Orders for store pickup are **Pending** by default and don't need to be accepted.

### Order fulfillment line actions

- **Edit** – If an order status is pending, it can be edited from the POS. Orders that have already been partially picked, packed, or invoiced can't be edited from the order fulfillment view.
- **Accept** – If **Manual accept** is configured at the channel level, lines must be first accepted before they can move through the order fulfillment process.
- **Pick** – The pick option supports several actions:
    - The **Picking** action updates the status of the order line so other store employees don't attempt to pick the same line.
    - The **Print picking list** action prints a picking list for the selected line or lines and also updates their status to **Picking**. Picking list formats are controlled as part of receipt formats. For more information about how to set up receipt formats, see [Receipt templates and printing](receipt-templates-printing.md).
    - The **Mark as picked** action indicates that the line has been picked. **Mark as picked** initiates corresponding inventory transactions in headquarters. Picking actions can be performed at the same time for multiple order lines across orders and for all modes of delivery.
- **Reject** – Lines or partial lines can be rejected, which allows them to be reassigned from headquarters to another store or warehouse. Lines can only be rejected if they haven't yet been picked or packed. To reject a line that has already been picked or packed, that line must be unpicked or unpacked from headquarters.
- **Pack** – The pack option supports two actions: **Print packing slip** prints a packing slip for the selected lines, and **Mark as packed** marks the lines as packed and delivered in headquarters. Only order lines that belong to the same order and have the same mode of delivery can be packed at the same time. Packing slip formats are controlled as part of receipt formats. For more information about how to set up receipt formats, see [Receipt templates and printing](receipt-templates-printing.md).
- **Ship** – The ship action marks selected lines as **Delivered** in headquarters. After a line is fully shipped, it no longer appears in the order fulfillment view.
- **Pickup** – The pickup action adds the lines to the transaction view for pickup. If there are other lines on the order that aren't being picked up, they're added to the transaction view with a quantity of zero. After a line is fully picked up, it no longer appears in the order fulfillment view.

### Order fulfillment filtering

Order fulfillment at the POS includes filtering to help the user easily find what they need. Filters can be changed on the Action Pane at the bottom of the **Point of sale** screen. By default, a **Delivery type** filter is applied, based on how the operation is set up. If the operation is set up with the parameter **All orders**, then that filter is applied when accessing order fulfillment. The same applies for the **Store pickup** and **Ship from store** parameters. Other filters that can be applied to the order fulfillment view include:

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
