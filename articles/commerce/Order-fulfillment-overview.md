---
# required metadata

title: Store order fulfillment
description: This topic provides an overview of store order fulfillment. 
author: BrianShook
ms.date: 10/30/2017
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  RetailStoreTable, RetailTillLayout
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 

ms.search.region: Global
ms.search.industry: retail
ms.author: brshoo
ms.search.validFrom: 2017-10-30
ms.dyn365.ops.version: 

---

# Store order fulfillment

[!include [banner](includes/banner.md)]

Many retailers would like to optimize order fulfillment by enabling stores to fill orders. Order fulfillment at the store level can help to ease overstock scenarios for a specific store, or may be needed from a logistical standpoint in cases where a store has extra capacity or is located within closer shipping distance to the customer. To address this need, a unified order fulfillment operation is available at the point of sale.

Orders for fulfillment at a specific store have the store's warehouse designated on the header or lines of the order.

The order fulfillment operation in the point of sale provides a single work area in the point of sale that can be used to process orders. This includes everything from accepting the order, to marking it as shipped, or initiating store pickup.

## Access unified order fulfillment in the point of sale

Order fulfillment, [Operation ID 928](pos-operations.md), can be used to access the store order fulfillment work area in the point of sale.

The order fulfillment operation does not have its own permission out-of-the-box, but in the future, users will be able to use the **Allow retrieve order** permission to invoke the operation from the point of sale.

At the store level, a configuration setting is available to determine whether an order line must be accepted manually from within the point of sale. If that configuration option is not set, order lines will be accepted by default. If that configuration option is turned on, users at the point of sale will need to select **Allow accept order** permission to accept orders from within the point of sale.

Order lines can also be rejected from the point of sale. Rejecting an order line signifies that it will not be fulfilled at that store and sends the order line back for reassignment to another store or warehouse. Order line rejection permission is granted through the **Allow order reject** permission.

## Order fulfillment operation parameters

Order fulfillment provides out-of-the-box parameters that can be applied to the operation when it is called in the point of sale. When the **All orders** parameter is configured, all orders are shown when the operation is used. The **Orders to ship** parameter shows only orders that must be shipped from the store and **Orders for pick up** shows orders that will be picked up in-store.

## Orders for fulfillment

The order fulfillment operation shows only orders that will either be picked up in or shipped from the current store. Orders for other stores to fulfill are not listed when using the order fulfillment operation.

## Line selection

Lines can be selected using the **Select** function in the Action Pane. When **Select** is enabled, multiple lines can be selected for processing. You can clear selected lines by clicking the same line again.

## Line details

Line details can be shown using the line details flyout menu. When this menu is used, three tabs are provided to show additional information for the selected line. The first tab, **Line details** shows details for the line itself such as quantity ordered and remaining. Additional details are provided including quantity picked, packed, and invoiced as well as mode of delivery and delivery address. The **Order details** tab provides order header information including customer, customer ID, order number, order total, and balance. The **Inventory** tab shows information for the selected line in terms of physical available inventory, reserved inventory and ordered inventory.

If multiple lines are selected, the order line details flyout menu will only indicate that multiple lines are selected. To show details for a single line, clear the lines until only one line remains.

## Pending order lines

Unified order fulfillment includes the ability to manually accept orders. By default, orders for fulfillment at the store are already accepted. However, if business processes dictate that a worker at the store level must accept orders, manual acceptance can be turned on at the retail store level. To enable order acceptance, go to **Retail and Commerce** \> **Channels** \> **Stores** \> **All stores**. Open the desired store and on the **General** tab, locate the **Order fulfillment** sub header. This sub header has a **Manual accept** option that is set to **No** by default. By setting this option to **Yes** and synchronizing the changes to the channel database, order lines can go through the acceptance process.

Workers with the **Allow accept order** permission can open order fulfillment and select lines for acceptance. Once lines have been accepted, their state changes from **Pending** to **Accepted** and the rest of the order fulfillment process can proceed. When **Manual accept** is turned on, orders will not be processed until they have been accepted.

Orders for store pickup never have the **Pending** state. This is done to avoid a scenario in which a customer arrives at the store and the order line cannot be processed because a worker with the proper privilege is not available.

## Accepted order lines

Orders with the line state **Accepted** can proceed through the rest of the order fulfillment process at the point of sale. After an order has been accepted, any remaining action can be taken against the order line.

For example, an accepted order line can be selected and then picked up directly without going through picking and packing.

## Line actions

### Pick

The **Pick** category of actions is provided to aid in the process of picking order lines from shelves. The picking action can only be performed on order lines that have been previously accepted.

**Action: Picking**

- **Resulting POS status:** Picking
- **Resulting back office status:** No change

After an order has been accepted, lines can be selected and marked as **Picking**. Marking a line as **Picking** is a way to indicate that the picking work is already being performed on a line. This prevents two workers from attempting to pick the same order lines at the same time.

**Action: Print picking list**

- **Resulting status:** Picking
- **Resulting back office status:** No change

Picking lists can be printed at the point of sale to assist workers performing the picking process. A printed picking list can be carried with the worker performing picking and as products are picked, the worker would manually mark them as picked on the picking list.

The picking list format is configured in Commerce and added to the receipt profile. For more information about setting up receipt
profiles, see [Receipt templates and printing](receipt-templates-printing.md).

If lines are selected and a picking list is printed for those lines, they are automatically updated with the **Picking** status.

**Action: Mark as picked**

- **Resulting status:** Picked or partially picked
- **Resulting back office status:** Picked or partially picked

After the physical picking process has been performed, lines can be marked as **Picked**. Selecting a line and marking it as **Picked** performs a real-time call to update the order line. After the line has been marked as **Picked** at the point of sale, the status in the back office is also updated to **Picked** and inventory transactions reflect that the specified quantity has been decremented.

When orders are processed over time, partial quantities can be processed for a specific line. If a line is selected and the action **Mark as picked** is taken, and the quantity is greater than one, the user is prompted for the quantity. The remaining quantity to be picked is auto-filled. If less than the remaining quantity is specified, the status of the line becomes **Partially picked**. When the order line is updated in the back office, it will also reflect the partially picked status and the quantity entered by the user is used for the inventory update.

If an order line is picked in error, the unpick process must be performed on the order line in the back office. There is currently no unpick action supported at the point of sale.

Orders lines from different orders can be selected and marked as **Picking**, printed on the same pick list, or marked as **Picked**.

### Pack

Order lines can be packed at any point after the order line has been accepted.

**Action: Print packing slip**

- **Resulting status:** Packed or partially packed
- **Resulting back office status:** Delivered or partially delivered

This action marks lines as packed or partially packed and prints a packing slip. A packing slip can be printed to validate the products that have been packed together. The packing slip format is configured in Commerce and added to the receipt profile. For more information about setting up receipt profiles, see [Receipt templates and printing](receipt-templates-printing.md).

**Action: Mark as packed**

- **Resulting status:** Packed or partially packed
- **Resulting back office status:** Delivered or partially delivered

The **Mark as packed** action can be used to indicate that lines are packed without printing a packing slip. Both **Print packing slip** and **Mark as packed** result in inventory transactions in the back office. Packing lines in the point of sale will result in packing slip journals being generated in the back office.

If an order line is packed in error, the packing slip journal must be corrected at the back office.

Only lines on the same order and with the same mode of delivery can be packed at the same time.

Currently, the option to mark store pickup lines as **Packed** is disabled. This capability will be added in a future release. The packing slip creation process will be enhanced to support injection of third-party shipping information into the packing slip process.

### Pick up

Orders for store pickup can be directly picked up once they are retrieved in the point of sale. Store pick up orders are not subject to acceptance.

**Action: Pick up**

- **Resulting status:** Invoiced or partially invoiced
- **Resulting back office status:** Invoiced or partially invoiced

If a line is selected for pick up from unified order fulfillment, the entire order is loaded into the point of sale and the full quantity for the selected line is marked. Other lines on the order are also loaded into the transaction view of the point of sale, but with quantity marked as zero.

After lines for pickup have been loaded into the transaction view, the transaction can be tendered as usual.

Lines that have been fully invoiced through pick up will no longer show up in unified order processing. Lines that have been partially picked up will continue to appear in unified order fulfillment until they have been picked up in full.

If a line is picked up in error, a return must be performed to correct the error.

Only lines on the same order and with the same mode of delivery can be picked up at the same time.

### Shipping

Order lines to be shipped from the store can be processed through unified order fulfillment using the **Ship** action. If manual order line acceptance is configured at the channel level, orders must be accepted prior to shipping. After an order line has been accepted and has a **Pending** or other status, lines can be shipped.

**Action: Ship**

- **Resulting status:** Invoiced or partially invoiced
- **Resulting back office status:** Invoiced or partially invoiced

Lines shipped from unified order fulfillment are invoiced from the back office similar to if the order is invoiced directly from the back office. Lines being shipped from unified order fulfillment are not loaded into the transaction view and there is no tendering performed at the time the lines are shipped.

Order lines that have been fully shipped no longer appear in unified order fulfillment. Partially shipped lines will continue to appear in unified order fulfillment until they have been shipped in full.

Only lines from the same order can be shipped at the same time. If the lines from the same order have different modes of deliver, they can still be selected for shipping at the same time.

### Reject

Lines or partial lines can be rejected. This allows them to be reassigned from the back office to another store or warehouse. Lines can only be rejected if they have not yet been picked or packed. To reject a line that has already been picked or packed, that line must be unpicked or unpacked from the back office.

**Action: Reject**

- **Resulting status:** Rejected
- **Resulting back office status:** No change

The rejected order lines can be viewed from the **Sales order processing and inquiry** workspace. Clear the person filter on the workspace to view all the rejected order lines across the stores. The **Rejected order lines** tab under the **Orders and favorites** section display the order line details. Additionally, the users can click the **Rejected order lines** button under the **Summary** section to navigate to a sales order view. This shows all the orders that have one or more rejected order lines. If Distributed Order Management (DOM) is enabled, then these rejected orders will be automatically reassigned to the appropriate stores for fulfillment, however, these order lines can be manually reassigned as well. To do so, select the line that shows the **Fulfillment status** as **Rejected** and change the site/warehouse as needed. Click the **Update line** drop-down menu and click **Reset fulfillment status** to change the fulfillment status from **Rejected** to **Accepted** or **Pending** depending on the order fulfillment set up. After the fulfillment status is reset, then the store workers will be able to view the order lines in POS.

## Line quantity tracking

A single order line of quantity greater than one can be processed over time, resulting in multiple sub states for order lines. For example, if a builder has a project that required 500 boards, but the builder will only pick up or have a few boards delivered at a time over the course of the project, there could be quantities that are being picked, packed, and shipped at the same time.

Any time a line is selected, the remaining amount for the line will be auto-filled to assume that the remaining quantity is being processed. Using the above example, if 200 boards have already been picked and the line for boards is selected for picking, the remaining quantity of 300 will be automatically filled in the quantity. The same is true if 200 boards have already been invoiced. In that case, only the remaining quantity will be auto filled.

Continuing with the above example, if 200 boards are marked as packed and shipping is selected, the full amount of 500 will be autofilled. If only 200 boards are shipped, the system will assume that the previously packed boards are being shipped and the packed quantity will be decremented. If 201 boards are shipped, the packed boards are first decremented with the remaining single board being decremented from the quantity remaining.

## Line statuses

Order lines in the point of sale have several statuses to reflect the state of the order line. Statuses in the point of sale and back office do not match in all cases. Order line status can be viewed through the point of sale using the order fulfillment operations. In the back office, order lines can be viewed from the order details. Order details can be accessed through **Retail and Commerce** \> **Customers** \> **All customer orders**. Select the **Order ID** to view order details. From order details select the **Sales order** tab, then select **Detailed status** under the **View** subheader.

- **Pending** – Order lines that have been assigned to a store, but not yet accepted have the **Pending** status when viewed at the point of sale. Lines pending acceptance in the point of sale will have the **Order processing** status in the back office.
- **Accepted** – Order lines that have been manually accepted or automatically accepted will have the status of **Accepted** when viewed at the point of sale. Lines with the **Accepted** status will show as **Order processing** in the back office.
- **Picking** – Lines that are currently being picked at the store level have the status of **Picking**. Those same lines, when viewed at the back office, will show as **Order processing**.
- **Picked** and **Partially picked** – Lines that have been picked or partially picked at the point of sale will have the status **Picked** or **Partially picked**. The same lines in the back office will also show as **Picked** or **Partially picked**.
- **Packed** and **Partially packed** – Lines that have been packed or partially packed at the point of sale will have the status **Packed** or **Partially packed**. The same lines in the back office will also show as **Delivered** or **Partially delivered**.
- **Partially invoiced** – Lines that have been partially picked up or partially shipped will have the status **Partially invoiced** at the point of sale and in the back office.
- **Invoiced** – Lines that have been fully invoiced at the point of sale will no longer show up for fulfillment. In the back office the status for those lines is **Invoiced**.

## Order fulfillment filtering

Order fulfillment at the point of sale includes filtering to help the user easily find what they need. Filters can be changed through the Action Pane at the bottom of the **Point of sale** screen. By default, a **Delivery type** filter is applied, based on how the operation is set up. If the operation is set up with the **All orders** parameter, then that filter is applied when accessing order fulfillment. The same applies for the **Store pickup** and **Ship from store** parameters. Other filters that can be applied to the order fulfillment view include:

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