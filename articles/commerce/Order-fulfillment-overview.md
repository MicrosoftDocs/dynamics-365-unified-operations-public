---
title: Store order fulfillment
description: This article provides an overview of store order fulfillment in Microsoft Dynamics 365 Commerce. 
author: BrianShook
ms.date: 01/23/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2017-10-30 
ms.custom: 
  - bap-template
---

# Store order fulfillment

[!include [banner](includes/banner.md)]

This article provides an overview of store order fulfillment in Microsoft Dynamics 365 Commerce.

Many retailers want to optimize order fulfillment by enabling stores to fill orders. Order fulfillment at the store level can help ease overstock scenarios for a specific store. From a logistical standpoint, order fulfillment might be needed when a store has extra capacity or is located within closer shipping distance to the customer. To address this need, a unified order fulfillment operation is available at the point of sale.

Orders for fulfillment at a specific store have the store's warehouse designated on the header or lines of the order.

The order fulfillment operation in the point of sale provides a single work area in the point of sale that you can use to process orders. This work area includes everything from accepting the order, to marking it as shipped, or initiating store pickup.

The following video provides an overview and demo of store fulfillment capabilities in Dynamics 365 Commerce.


> [!VIDEO https://learn-video.azurefd.net/vod/player?id=50c67f62-16a0-47e8-af5e-0d3e69f3da71]

## Access unified order fulfillment in the point of sale

Use the order fulfillment operation, [Operation ID 928](pos-operations.md), to access the store order fulfillment work area in the point of sale.

The order fulfillment operation doesn't have its own permission out-of-the-box, but in the future, users can use the **Allow retrieve order** permission to invoke the operation from the point of sale.

At the store level, a configuration setting determines whether an order line must be accepted manually from within the point of sale. If you don't set that configuration option, order lines are accepted by default. If you turn on that configuration option, users at the point of sale need to select **Allow accept order** permission to accept orders from within the point of sale.

Users can also reject order lines from the point of sale. Rejecting an order line signifies that it isn't fulfilled at that store and sends the order line back for reassignment to another store or warehouse. Order line rejection permission is granted through the **Allow order reject** permission.

## Order fulfillment operation parameters

Order fulfillment provides predefined parameters that you can apply to the operation when you call it in the point of sale. When you configure the **All orders** parameter, the operation shows all orders. The **Orders to ship** parameter only shows orders that must be shipped from the store, and **Orders for pick up** shows orders that customers pick up in-store.

## Orders for fulfillment

The order fulfillment operation shows only orders that customers either pick up in or ship from the current store. The operation doesn't list orders for other stores to fulfill.

## Line selection

Use the **Select** function in the Action Pane to select lines. When **Select** is enabled, you can select multiple lines for processing. You can clear selected lines by selecting the same line again.

## Line details

Use the line details flyout menu to show line details. This menu provides three tabs that show additional information for the selected line. The first tab, **Line details**, shows details for the line itself, such as quantity ordered and remaining. It provides additional details including quantity picked, packed, and invoiced, as well as mode of delivery and delivery address. The **Order details** tab provides order header information, including customer, customer ID, order number, order total, and balance. The **Inventory** tab shows information for the selected line in terms of physical available inventory, reserved inventory, and ordered inventory.

If you select multiple lines, the order line details flyout menu only indicates that multiple lines are selected. To show details for a single line, clear the lines until only one line remains.

## Pending order lines

Unified order fulfillment includes the ability to manually accept orders. By default, the system already accepts orders for fulfillment at the store. However, if your business processes dictate that a worker at the store level must accept orders, you can turn on manual acceptance at the retail store level. To enable order acceptance, go to **Retail and Commerce** \> **Channels** \> **Stores** \> **All stores**. Open the desired store. On the **General** tab, locate the **Order fulfillment** subheader. This subheader has a **Manual accept** option that is set to **No** by default. Set this option to **Yes** and synchronize the changes to the channel database. Order lines can go through the acceptance process.

Workers with the **Allow accept order** permission can open order fulfillment and select lines for acceptance. Once workers accept lines, their state changes from **Pending** to **Accepted** and the rest of the order fulfillment process can proceed. When **Manual accept** is turned on, the system doesn't process orders until it accepts them.

Orders for store pickup never have the **Pending** state to avoid a scenario in which a customer arrives at the store and the order line can't be processed because a worker with the proper privilege isn't available.

## Accepted order lines

The system accepts orders with the line state **Accepted**. These orders can proceed through the rest of the order fulfillment process at the point of sale. After an order is accepted, you can take any remaining action against the order line.

For example, you can select an accepted order line and then pick it up directly without going through picking and packing.

## Line actions

### Pick

The **Pick** category of actions helps you pick order lines from shelves. You can only perform the picking action on order lines that you previously accepted.

**Action: Picking**

- **Resulting POS status:** Picking
- **Resulting headquarters status:** No change

After you accept an order, you can select lines and mark them as **Picking**. When you mark a line as **Picking**, you indicate that the picking work is already being performed on that line. This status prevents two workers from attempting to pick the same order lines at the same time.

**Action: Print picking list**

- **Resulting status:** Picking
- **Resulting headquarters status:** No change

Print picking lists at the point of sale to assist workers performing the picking process. The worker performing picking can carry a printed picking list, and as products are picked, the worker manually marks them as picked on the picking list.

The picking list format is configured in Commerce and added to the receipt profile. For more information about setting up receipt
profiles, see [Receipt templates and printing](receipt-templates-printing.md).

If you select lines and print a picking list for those lines, the system automatically updates the lines with the **Picking** status.

**Action: Mark as picked**

- **Resulting status:** Picked or partially picked
- **Resulting headquarters status:** Picked or partially picked

After you perform the physical picking process, mark the lines as **Picked**. When you select a line and mark it as **Picked**, the system makes a real-time call to update the order line. After you mark the line as **Picked** at the point of sale, the status in headquarters is also updated to **Picked** and inventory transactions reflect that the specified quantity is decremented.

When orders are processed over time, partial quantities can be processed for a specific line. If you select a line and take the action **Mark as picked**, and the quantity is greater than one, the system prompts you for the quantity. The remaining quantity to be picked is autofilled. If you specify less than the remaining quantity, the status of the line becomes **Partially picked**. When the order line is updated in headquarters, it also reflects the partially picked status and the quantity you entered is used for the inventory update.

If you pick an order line in error, you must perform the unpick process on the order line in headquarters. Currently, the point of sale doesn't support an unpick action.

You can select order lines from different orders and mark them as **Picking**, print them on the same pick list, or mark them as **Picked**.

### Pack

You can pack order lines anytime after you accept the order line.

**Action: Print packing slip**

- **Resulting status:** Packed or partially packed
- **Resulting headquarters status:** Delivered or partially delivered

This action marks lines as packed or partially packed and prints a packing slip. You can print a packing slip to validate the products that are packed together. The Commerce configures the packing slip format and adds it to the receipt profile. For more information about setting up receipt profiles, see [Receipt templates and printing](receipt-templates-printing.md).

**Action: Mark as packed**

- **Resulting status:** Packed or partially packed
- **Resulting headquarters status:** Delivered or partially delivered

Use the **Mark as packed** action to indicate that lines are packed without printing a packing slip. Both **Print packing slip** and **Mark as packed** result in inventory transactions in headquarters. When you pack lines in the point of sale, packing slip journals are generated in headquarters.

If you pack an order line in error, you must correct the packing slip journal in headquarters.

You can only pack lines that are on the same order and have the same mode of delivery.

Currently, the option to mark store pickup lines as **Packed** is disabled. This capability will be added in a future release. The packing slip creation process will be enhanced to support injection of partner shipping information into the packing slip process.

### Pick up

You can pick up orders for store pickup as soon as the point of sale retrieves them. The system doesn't require acceptance for store pick up orders.

**Action: Pick up**

- **Resulting status:** Invoiced or partially invoiced
- **Resulting headquarters status:** Invoiced or partially invoiced

If you select a line for pick up from unified order fulfillment, the point of sale loads the entire order and marks the full quantity for the selected line. The point of sale also loads other lines on the order into the transaction view, but it marks their quantity as zero.

After the transaction view loads the lines for pickup, you can tender the transaction as usual.

Lines that the pickup process fully invoices no longer appear in unified order processing. Lines that the pickup process partially invoices continue to appear in unified order fulfillment until the system invoices them in full.

If you pick up a line in error, you must perform a return to correct the error.

You can only pick up lines that share the same order and mode of delivery at the same time.

### Shipping

You can process order lines to ship from the store through unified order fulfillment by using the **Ship** action. If you configure manual order line acceptance at the channel level, you must accept orders before shipping. After you accept an order line and it has a **Pending** or other status, you can ship lines.

**Action: Ship**

- **Resulting status:** Invoiced or partially invoiced
- **Resulting headquarters status:** Invoiced or partially invoiced

When you ship lines from unified order fulfillment, headquarters invoices the lines similar to if headquarters invoices the order directly. Lines that you ship from unified order fulfillment don't load into the transaction view and there's no tendering performed at the time you ship the lines.

Fully shipped order lines no longer appear in unified order fulfillment. Partially shipped lines continue to appear in unified order fulfillment until they're shipped in full.

You can only ship lines from the same order at the same time. If the lines from the same order have different modes of deliver, you can still select them for shipping at the same time.

### Reject

You can reject lines or partial lines, which allows them to be reassigned from headquarters to another store or warehouse. You can only reject lines if they aren't yet picked or packed. To reject a line that is already picked or packed, you must unpick or unpack that line from headquarters.

**Action: Reject**

- **Resulting status:** Rejected
- **Resulting headquarters status:** No change

You can view the rejected order lines from the **Sales order processing and inquiry** workspace. To view all the rejected order lines across the stores, clear the person filter on the workspace. The **Rejected order lines** tab under the **Orders and favorites** section displays the order line details. Additionally, users can select **Rejected order lines** under the **Summary** section to navigate to a sales order view, which shows all the orders that have one or more rejected order lines. If Distributed Order Management (DOM) is enabled, then these rejected orders are automatically reassigned to the appropriate stores for fulfillment. However, you can manually reassign these order lines. To do so, select the line that shows the **Fulfillment status** as **Rejected** and change the site or warehouse as needed. Select the **Update line** drop-down menu and select **Reset fulfillment status** to change the fulfillment status from **Rejected** to **Accepted** or **Pending** depending on the order fulfillment setup. After you reset the fulfillment status, the store workers can view the order lines in POS.

## Line quantity tracking

You can process a single order line with a quantity greater than one over time, which results in multiple sub states for order lines. For example, if a builder has a project that requires 500 boards, but the builder only picks up or has a few boards delivered at a time over the course of the project, the quantities can be in the picking, packing, and shipping states at the same time.

When you select a line, the system autofills the remaining amount for the line, assuming that the remaining quantity is being processed. From the preceding example, if 200 boards are already picked and you select the line for boards for picking, the remaining quantity of 300 is automatically filled in. The same is true if 200 boards are already invoiced. In that case, only the remaining quantity is autofilled.

From with the preceding example, if you mark 200 boards as packed and select shipping, the full amount of 500 is autofilled. If you ship only 200 boards, the system assumes that the previously packed boards are being shipped and the packed quantity is decremented. If you ship 201 boards, the packed boards are first decremented with the remaining single board being decremented from the quantity remaining.

## Line statuses

Order lines in the point of sale have several statuses to reflect the state of the order line. Statuses in the point of sale and headquarters don't match in all cases. You can view order line status through the point of sale by using the order fulfillment operations. In headquarters, you can view order lines from the order details. You can access order details through **Retail and Commerce** \> **Customers** \> **All customer orders**. Select the **Order ID** to view order details. From order details select the **Sales order** tab, then select **Detailed status** under the **View** subheader.

- **Pending** – When viewed at the point of sale, order lines that are assigned to a store, but not yet accepted have the **Pending** status. Lines pending acceptance in the point of sale show the **Order processing** status in headquarters.
- **Accepted** – When viewed at the point of sale, order lines that are manually accepted or automatically accepted have the status of **Accepted**. Lines with the **Accepted** status show as **Order processing** in headquarters.
- **Picking** – Lines that are currently being picked at the store level have the status of **Picking**. Those same lines, when viewed in headquarters, show as **Order processing**.
- **Picked** and **Partially picked** – Lines that are picked or partially picked at the point of sale have the status **Picked** or **Partially picked**. The same lines in headquarters also show as **Picked** or **Partially picked**.
- **Packed** and **Partially packed** – Lines that are packed or partially packed at the point of sale have the status **Packed** or **Partially packed**. The same lines in headquarters also show as **Delivered** or **Partially delivered**.
- **Partially invoiced** – Lines that are partially picked up or partially shipped have the status **Partially invoiced** at the point of sale and in headquarters.
- **Invoiced** – Lines that are fully invoiced at the point of sale no longer show up for fulfillment. In headquarters the status for those lines is **Invoiced**.

## Order fulfillment filtering

Order fulfillment at the point of sale includes filtering to help the user easily find what they need. Change filters through the Action Pane at the bottom of the **Point of sale** screen. By default, the system applies a **Delivery type** filter, based on how the operation is set up. If the operation is set up with the **All orders** parameter, the system applies that filter when you access order fulfillment. The same condition applies for the **Store pickup** and **Ship from store** parameters. You can apply other filters to the order fulfillment view, including filters for:

- Customer number
- Customer name
- Customer email
- Order number
- Mode of delivery
- Receipt number
- Channel reference ID
- Originating store number
- Line status
- Created date
- Delivery date
- Receipt date

[!INCLUDE[footer-include](../includes/footer-banner.md)]
