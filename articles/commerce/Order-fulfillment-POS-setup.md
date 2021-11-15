---
# required metadata

title: Set up order fulfillment for stores
description: This topic provides an overview of how to set up store order fulfillment. 
author: BrianShook
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  RetailStoreTable, RetailTillLayout
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: brshoo
ms.search.validFrom: 2017-10-30
ms.dyn365.ops.version: 


---


# Set up order fulfillment for stores

[!include [banner](includes/banner.md)]

Many retailers would like to optimize order fulfillment by enabling stores to fill orders. Order fulfillment at the store level can help to ease overstock scenarios for a specific store, or may be needed from a logistical standpoint in cases where a store has extra capacity or is located within closer shipping distance to the customer. To address this need, a unified order fulfillment operation is available at the point of sale.

Orders for fulfillment at a specific store has the store's warehouse designated on the header or lines of the order.

The order fulfillment operation in the point of sale provides a single work area in the point of sale that can be used to process orders. This includes everything from accepting the order, to marking it as shipped, or initiating store pickup.

## Set up the order fulfillment operation

Order fulfillment, [Operation ID 928](pos-operations.md), can be used to access the store order fulfillment work area in the point of sale.

Follow the steps in [Add the operation to a button grid](pos-screen-layouts.md) to specify which parameter to use when invoking order fulfillment at the point of sale. By default, after specifying the order fulfillment operations, the **All orders** is selected. When configured with this parameter, the operation will list all order lines for fulfillment at the current store. Also available is **Orders to ship**, which can be assigned to a button and utilized when the user only wants to see orders that will ship out of the store. Finally, there is **Orders for pick up**. When invoked at the point of sale, this only lists orders to be picked up at the store. The different parameters can be assigned to different buttons to give the user a variety of ways to view order fulfillment.

### Enable users to access order fulfillment at the point of sale

The order fulfillment operation does not have its own permission out-of-the-box, but in the future, users may require the **Allow retrieve order** permission to invoke the operation from the point of sale.

At the store level, a configuration setting is available to determines whether an order line must be accepted manually from within the point of sale. If that configuration option is not set, order lines will be accepted by default. If that configuration option is turned on, users at the point of sale will need to have the **Allow accept order** permission to accept orders from within the point of sale.

### Enable manual order acceptance

Be default, order lines assigned to a store are marked as **Accepted**. This means that it is assumed they will be fulfilled from the assigned store and will not be subject to further assignment. In certain cases, retailers may want to manually accept orders before they can be fulfilled. For example, if a store is short staffed and is unable to fulfill orders, a store manager will only accept as many orders for processing as they feel can adequately be processed in a given day. Until an order is accepted, it may be reassigned by the back office to a different store. In this way, order acceptance also provides a way to indicate that an order has been acknowledged by a store and will be fulfilled.

Order lines for store pickup are marked as **Pending** and are not subject to acceptance.

To turn on manual acceptance for order lines, navigate to **Retail and Commerce** \> **Channels** \> **Stores** \> **All stores**. Select the store and click in the store ID to view the store's details. Click **Edit**. On the **General** FastTab, locate the **Order fulfillment** subheader and change **Manual accept** from **No** to **Yes**.

### Enable reject order line capability

Order lines can also be rejected from the point of sale. Rejecting an order line signifies that it will not be fulfilled at that store and sends the order line back for reassignment to another store or warehouse. Order line rejection permission is granted through the **Allow reject order** permission in the POS permission group associated with the worker. While rejecting a line, the retailers can mandate their workers to provide a reason for rejection. This can be achieved by using info codes of **Info code activity** type **Order fulfillment** and assigning the info code to **Reject order line** in the functionality profile associated with the channel.

> [!NOTE]
> Only the info codes of **Info code activity** type **Order fulfillment** can be assigned to the **Reject order line** action.

### Synchronize changes to the channel database

After the operation has been assigned to a button grid, the proper permissions have been assigned, and the channel is configured, the changes must be synchronized to the channel database. To do so, navigate to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**. Select schedule "1090-Registers" to sync button grid changes and then click **Run now**. Next, sync permissions changes by selecting "1060-Staff" and then click **Run now**. Next, sync channel changes by selecting "1070-Channel configuration" and click **Run now**. Finally, sync the newly created info code for reject reason by selecting the "1110-Global configuration" and click **Run now**.

## Use order fulfillment at the point of sale

Open the point of sale and select the order fulfillment operation. Depending on how it is configured, either all lines, order lines for pickup, or order lines to ship will be listed.

### Order fulfillment view

The order fulfillment view lists order lines for fulfillment at the store and includes the following columns:

- Order number
- Product number
- Description
- Quantity ordered
- Requested delivery date
- Customer name
- Fulfillment status

Additional information for a specific order line can be viewed by selecting the order line and then opening the flyout menu located just below the logged in user/shift information shown in the point of sale header. This menu includes 2 tabs: one for line details and another for order details. The line details tab includes the following information:

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

At the bottom of the order fulfillment view is an Action Pane. This contains all of the actions that can be taken against an order line. If an action is not available based on a line's status, that action will be unavailable.

By default, orders will have a status of **Accepted**. Order status can be viewed as a column in the list of order lines. If **Manual accept** is configured at the channel level, all lines to be shipped will show as **Pending** and must be accepted before they can be fulfilled. Orders for store pickup are **Pending** by default and do not need to be accepted.

### Order fulfillment line actions

- **Edit** – If an order status is pending, it can be edited at the point of sale. Orders that have already been partially picked, packed, or invoiced cannot be edited from the order fulfillment view.
- **Accept** – If **Manual accept** is configured at the channel level, lines must be first accepted before they can move through the order fulfillment process.
- **Pick** – The pick option supports several actions. First, **Picking** updates the status of the order line so others in the store do not attempt to pick the same line. Next, **Print picking list** prints a picking list for the selected line or lines and also updates their status to **Picking**. Picking list formats are controlled as part of receipt formats. For more information about how to set up receipt formats, see [Receipt templates and printing](receipt-templates-printing.md). Finally, **Mark as picked** indicates the line has been picked. **Mark as picked** initiates corresponding inventory transactions in the back office. Picking actions can be performed at the same time for multiple order lines across orders and for all modes of delivery.
- **Reject** – Lines or partial lines can be rejected. This allows them to be reassigned from the back office to another store or warehouse. Lines can only be rejected if they have not yet been picked or packed. To reject a line that has already been picked or packed, that line must be unpicked or unpacked from the back office.
- **Pack** – The pack option supports two actions: **Print packing slip** will print a packing slip for the selected lines and **Mark as packed** will and mark the lines as packed and mark the lines as delivered in the back office. Only order lines that belong to the same order and have the same mode of delivery can be packed at the same time. Packing slip formats are controlled as part of receipt formats. For more information about how to set up receipt formats, see [Receipt templates and printing](receipt-templates-printing.md).
- **Ship** – The ship action will mark selected lines as **Delivered** in the back office. After a line has been fully shipped, it will no longer appear in the order fulfillment view.
- **Pickup** – The pickup action adds the lines to the transaction view for pickup. If there are other lines on the order that aren't currently being picked up, they will be added to the transaction view with quantity zero. After a line has been fully picked up, it will no longer appear in the order fulfillment view.

### Order fulfillment filtering

Order fulfillment at the point of sale includes filtering to help the user easily find what they need. Filters can be changed on the Action Pane at the bottom of the **Point of sale** screen. By default, a **Delivery type** filter is applied, based on how the operation is set up. If the operation is set up with the parameter **All orders**, then that filter is applied when accessing order fulfillment. The same applies for the **Store pickup** and **Ship from store** parameters. Other filters that can be applied to the order fulfillment view include:

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
