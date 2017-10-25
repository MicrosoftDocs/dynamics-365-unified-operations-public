---
# required metadata

title: Store fulfillment
description: This topic provides an overview for store order fulfillment. 
author: rubencdelgado
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Pick one: Application User/Developer/IT Pro]
# ms.devlang: 
# ms.reviewer: [Content Strategist microsoft alias]
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: 

---

# Order fulfillment in the Point of Sale

Many retailers would like to optimize order fulfillment byaenabling stores to fill orders. Order fulfillment at the store level can help
to ease overstock scenarios for a specific store, or may be desirable from a logistical standpoint in cases where a store has extra
capacity or is located within closer shipping distance to the customer. To address this need, a unified order fulfillment operation is
available at the point of sale.

Orders for fulfillment at a specific store will have the store's warehouse designated on the header or lines of the order. 

The order fulfillment operation in the point of sale provides a single work area in the point of sale that can be used to process orders from accepting the order to marking it as shipped or initiating store pickup. 

## Accessing unified order fulfillment in the point of sale

Operation ID 928, “Order fulfillment”, can be added to a point of sale button grid to access the unified order fulfillment page in the
point of sale. This operations is bound by the following permissions: 

  - Allow create order
  - Allow edit order
  - Allow retrieve order
  - Allow accept order 
  - Allow reject order

The operations ‘Allow accept order’ and ‘Allow reject order’ were created specifically for the unified order fulfillment operations, while the others are previously existing operations that have been extended to the ‘Allow accept order’ operation as applicable. 

## Parameters for the Order fulfillment operation

‘Order fulfillment’ provides out of the box parameters that can be applied to the operation when it is called in the point of sale. When the parameter, ‘All orders’, is configured, all orders are shown when the operation is used. The parameter ‘Orders to ship’ shows only orders that must be shipped from the store and ‘Orders for pick up’ shows orders that will be picked up in-store. 

## Orders for fulfillment

The ‘Order fulfillment’ operation shows only orders that will either be picked up in or shipped from the current store. Orders for other
stores to fulfill are not listed when using the order fulfillment operation. 

## Line selection

Lines may be selected using the ‘Select’ function in the action pane. When ‘Select’ is enabled, multiple lines may be selected for
processing. Selected lines may be deselected by clicking on the same line again. 

## Line details

Line details may be shown using the line details flyout. When the line details flyout is used, two tabs are provided to show additional
information for the selected line. The first tab, ‘Line details’ shows details for the line itself such as quantity ordered and remaining. Additional details are provided including quantity picked, packed and invoiced as well as mode of
delivery and delivery address. The ‘Order details’ tab provides order header information including customer and customer ID, order number, order total and balance.

If multiple lines are selected, the order line details flyout will only indicate that multiple lines are selected. To show details for a
single line, lines should be deselected until only one line is remaining. 

## Pending order lines

Unified order fulfillment includes the ability to manually accept orders. By default, orders for fulfillment at the store are already
accepted. However, if business processes dictate that a worker at the store level must accept orders, manual acceptance can be turned on at the retail store level. To enable order acceptance, navigate to Retail > Channels > Retail stores > All retail stores. Open the desired store and on the ‘General’ tab, locate the ‘Order fulfillment’ sub header. This sub header has a ‘Manual accept’ configuration option that is set to ‘No’ by default. By setting this option to ‘Yes’ and synchronizing the changes to the channel database, order lines can go through the acceptance process.

Workers with the permission ‘Allow accept order’ can open order fulfillment and select lines for acceptance. Once lines have been accepted, their state changes from ‘Pending’ to ‘Accepted’ and the rest of the order fulfillment process may proceed. When ‘Manual accept’ is turned on, orders may not be process until they have been accepted. 

Orders for store pickup never have the ‘Pending’ state. This is done to avoid a scenario in which a customer arrives at the store and the order line cannot be processed because a worker with the proper privilege is not available.

## Accepted order lines

Orders with the line state ‘Accepted’ may be proceed through the rest of the order fulfillment process at the point of sale. Once an order has been accepted, any remaining action can be taken against the order line. 

For example, an accepted order line can be selected and then picked up directly without going through picking and packing.

## Line actions

### Pick

The  ‘Pick’ category of actions is provided to aid in the process of picking order lines from shelves. The picking action can only be performed on order lines that have been previously accepted. 

**Action: Picking**
  Resulting POS status: Picking
  Resulting back office status: No change

Once an order has been accepted, lines may be selected and marked as ‘Picking’. Marking a line as ‘Picking’ is a way to indicate that the picking work is already being performed on a line. This prevents two workers from attempting to pick the same order lines at the same time.  

**Action: Print picking list**
  Resulting status: Picking
  Resulting back office status: No change

Picking lists can be printed at the point of sale to assist workers performing the picking process. A printed picking list can be carried with the worker performing picking and as products are picked, the worker would manually mark them as picked on the picking list. 

The picking list format is configured in Dynamics 365 and added to the receipt profile. For more information about setting up receipt
profiles, see: https://technet.microsoft.com/en-us/library/hh597197.aspx

If lines are selected and a picking list is printed for those lines, they are automatically updated with the status ‘Picking’. 

**Action: Mark as picked**
  Resuting status: Picked or Partially picked
  Resulting back office status: Picked or Partially picked

Once the physical picking process has been performed, lines can be marked as ‘Picked’. Selecting a line and marking it as ‘Picked’ performs a real-time call to update the order line in Dynamics 365 for Retail. After the line has been marked as ‘Picked’ at the point of sale, the status in the back office is updated to ‘Picked’ as well and inventory transactions reflect that the specified quantity has been decremented.

When orders are processed over time, partial quantities may be processed for a specific line. If a line is selected and the action ‘Mark as picked’ is taken, and the quantity is greater than one, the user is prompted for the quantity. The remaining quantity to be picked is auto-filled. If less than the remaining quantity is specified, the status of the line becomes ‘Partially picked’. When the order line is updated in the back office, it will also reflect the partially picked status and the quantity entered by the user is used for the inventory update. 

If an order line is picked in error, the unpick process must be performed on the order line in the back office. There is currently no ‘Unpick’ action supported at the point of sale. 

Orders lines from different orders may selected and marked as ‘Picking’, printed on the same pick list or marked as ‘Picked’. 

## Pack

Order lines may be packed at any point after the order line has been accepted. 

**Action: Print packing slip**
  Resuting status: Packed or Partially packed
  Resulting back office status: Delivered or Partially delivered

This action marks lines as packed or partially packed and prints a packing slip. A packing slip can be printed to validate the products that have been packed together. The packing slip format is configured in Dynamics 365 and added to the receipt profile. For more information about setting up receipt profiles, see: https://technet.microsoft.com/en-us/library/hh597197.aspx

**Action: Mark as packed**
  Resuting status: Packed or Partially packed
  Resulting back office status: Delivered or Partially delivered

The ‘Mark as packed’ action can be used to indicate that lines are packed without printing a packing slip. Both ‘Print packing slip’ and
‘Mark as packed’ result in inventory transactions in the back office. Packing lines in the point of sale will result in packing slip journals being generated in the back office. 

If an order line is packed in error, the packing slip journal must be corrected at the back office. 

Only lines on the same order and with the same mode of delivery can be packed at the same time. 

## Pick up

Orders for store pickup may be directly picked up once they are retrieved in the point of sale. Store pick up orders are not subject to
acceptance. 

**Action: Pick up**
  Resuting status: Invoiced or partially invoiced
  Resulting back office status: Invoiced or partially invoiced

If a line is selected for pick up from unified order fulfillment, the entire order is loaded into the point of sale and the full quantity for the selected line is marked. Other lines on the order are also loaded into the transaction view of the point of sale, but with quantity marked as zero. 

Once lines for pickup have been loaded into the transaction view, the transaction can be tendered as usual. 

Lines that have been fully invoiced through pick up will no longer show up in unified order processing. Lines that have been partially picked up will continue to appear in unified order fulfillment until they have been
picket up in full. 

If a line is picked up in error, a return must be performed to correct the error.  

Only lines on the same order and with the same mode of delivery can be picked up at the same time. 

## Shipping

Order lines to be shipped from the store can be processed through unified order fulfillment using the ‘Ship’ action. If manual order line acceptance is configured at the channel level, orders must be accepted prior to shipping. Once an order line has been accepted and has a ‘Pending’ or other status, lines may be shipped. 

**Action: Ship**
  Resuting status: Invoiced or partially invoiced
  Resulting back office status: Invoiced or partially invoiced

Lines shipped from unified order fulfillment are invoiced from the back office similar to if the order is invoiced directly from the back office. Lines being shipped from unified order fulfillment are not loaded into the transaction view and there is no tendering performed at the time the lines are shipped. 

Order lines that have been fully shipped no longer appear in unified order fulfillment. Partially shipped lines will continue to appear in unified order fulfillment until they have been shipped in full. 

Only lines from the same order may be shipped at the same time. If the lines from the same order have different modes of deliver, they may still be selected for shipping at the same time. 

## Line quantity tracking

A single order line of quantity greater than one may be processed over time, resulting in multiple sub states for order lines. For example, if a builder has a project that required 500 boards, but the builder will only pick up or have a few boards delivered over the course of the project, there could be quantities that are being picked, packed and shipped at the same time. 

Any time a line is selected, the remaining amount for the line will be auto-filled to assume that the remaining quantity is being processed.Using the above example, if 200 boards have already been picked and the line for boards is selected for picking, the remaining quantity will be automatically filled in the quantity dialog. The same is true if 200 boards have already been invoiced. In that case, only the remaining quantity will be auto filled. 

Continuing with the above example, if 200 boards are marked as packed and shipping is then selected, the full amount of 500 will be autofilled. If only 200 boards are shipped, the system will assume that the previously packed boards are being shipped and the packed quantity will be decremented. If 201 boards are shipped, the packed boards are first decremented with the remaining single board being decremented from the quantity remaining. 

## Line statuses explained

Order lines in the point of sale have several statuses to reflect the state of the order line. Statuses in the point of sale and back office do not match in all cases. Order line status can be viewed through the point of sale using the order fulfillment operations. In the back office, order lines can be viewed from the order details. Order details can be accessed through Retail > Customers > All customer orders. Select the order ID to view order details. From order details select the sales order tab, then 'Detailed status' under the 'View' subheader. 

**Pending**- Order lines that have been assigned to a store, but not yet accepted with have the "Pending" status when viewed at the point of sale. Lines pending acceptance in the point of sale will have the "Order processing" status in the back office.

**Accepted**- Order lines that have been manually accepted or automatically accepted will have the status of "Accepted" whenviewed at the point of sale. Lines with the "Accepted" status will show as "Order processing" in the back office.

**Picking**- Lines that are currently being picked at the store level have the status of "Picking". Those same lines, when viewed at the back office, will show as "Order processing".

**Picked and Partially picked**- Lines that have been picked or partially picked at the point of sale will have the status "Picked" or "Partially picked". The same lines in the back office will also show as "Picked" or "Partially picked".

**Packed and Partially packed**- Lines that have been packed or partially packed at the point of sale will have the status "Packed" or "Partially packed". The same lines in the back office will also show as "Delivered" or "Partially delivered".

**Partially invoiced**- Lines that have been partially picked up or partially shipped will have the status "Partially invoiced" at the point of sale and in the back office.

**Invoiced** Lines that have been fully invoiced at the point of sale will no longer show up for fulfillment. In the back office the status for those lines is "Invoiced".


