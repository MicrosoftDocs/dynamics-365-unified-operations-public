---
title: Calculate requested ship dates for purchase orders (preview)
description: This article describes how the system calculates requested ship dates for purchase orders. It also explains how to set up this calculation.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: VendCustTransportPoint2Point, SrmParameters, VendTable
ms.topic: how-to
ms.date: 11/16/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Calculate requested ship dates for purchase orders (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

Purchase orders in Microsoft Dynamics 365 Supply Chain Management can include both a *requested receipt date*, which specifies when the order should be received at your company's location, and a *requested ship date*, which specifies when the vendor should ship from their location. The system calculates requested ship dates based on the requested receipt date, lead time, the transport days setup, the vendor ship calendar, and other settings. The transport days setup lets you define the number of days that are required to transport items between pairs of addresses. Vendor ship calendars define the days when each vendor can ship.

If any of your vendors don't have specific delivery terms (such as delivery duty paid, delivery at place, or delivery at place unloaded), you must tell them when they should ship.

When master planning suggests a date for placing a planned order, it also considers the transport days setup. This approach helps ensure that the goods arrive on time.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

Before you can calculate requested ship dates, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management version 10.0.38 or later.
- The feature that's named *Supplier requested and confirmed shipment dates* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must be using Planning Optimization, not the [deprecated master planning engine](deprecated-master-planning-overview.md).

## Requested and confirmed receipt dates on purchase orders

As of Supply Chain Management version 10.0.38, the following date fields for purchase orders have been renamed so that they're better aligned with similar date fields for sales orders. The new names also help make it clear that the fields indicate the dates when the items will be *received* at your location, not when they're *sent* from the vendor's location.

- **Requested delivery date** is now labeled **Requested receipt date**.
- **Confirmed delivery date** is now labeled **Confirmed receipt date**.

## <a name="parameters"></a>Specify whether requested ship dates can be in the past

Sometimes, because of your requested receipt date, plus the lead time, transport days, vendor ship calendar, and other settings, the system might calculate a requested ship date that's in the past. To specify how the system handles this situation, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**.
1. On the **Delivery** tab, in the **Requested ship date in the past** field, select one of the following values:

    - *None* – Always allow requested ship dates to be in the past, without showing a warning.
    - *Allow with warning* – Allow requested ship dates to be in the past, but show a warning message to users when this situation occurs.
    - *Disallow with warning* – Always find the next earliest ship date that's after the current date, and show a warning message to users when this situation occurs.

## Set up purchase transport days

To define the number of days that are required to transfer goods between addresses, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Follow one of these steps:

    - To use an existing record, use the filters at the top of the grid to find it. To edit the record that you find, select the link in the **Shipping country/region** column. To delete the record, select it, and then select **Delete** on the Action Pane.
    - To create a new record, on the Action Pane, select **New**.

1. On the details page for the new or selected record, on the **General** tab, use the fields to define the shipping address, the receiving address, and the number of days that are required to transport goods between them. For more information about each field, hover over its label to open a tooltip.

    > [!TIP]
    > - When you must enter an address, first enter a value in the **Shipping ZIP/postal code** field. Often, the system can automatically fill in the rest of the address fields for you, based on the postal code.
    > - To calculate the ship date, the system uses the most specific purchase transport days record that it can find. For example, you have two purchase transport days records: one that specifies 30 days from Spain to the United States and another that specifies 20 days from Madrid to New York. In this case, a purchase order that's shipped from Madrid to New York uses 20 days, whereas an order from Valencia to New York uses 30 days.
    > - The shipping address takes precedence over receiving address if there is an equal priority.

1. On the **Transport days per mode of delivery** FastTab, you can set specific transport days for any number of delivery modes (such as road, rail, and air). Use the buttons on the toolbar to add and remove rows in the grid as you require.

    - For each row, select a mode of delivery, and then specify the number of transport days for that mode.
    - If you want one of the modes of delivery to define the default transport days that apply to any modes that aren't specified in the grid, select the **Default** checkbox for that mode's row.
    - If the **Default** checkbox isn't selected for any row, the **Transport in days** value that's specified on the **General** FastTab is used as the default travel time.

1. On the Action Pane, select **Save**.

## Vendor settings for calculating requested ship dates

To calculate requested ship dates, you must set up an address for each vendor. To help make the calculation more accurate, you can also set up vendor ship calendars that define specific days when each vendor can ship.

### Set up vendor addresses

To set up addresses for a vendor, follow these steps.

1. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**.
1. Open the vendor record that you want to work with.
1. On the **Addresses** FastTab, add and remove addresses as you require. If more than one address is specified on the **Addresses** FastTab, when the system uses the purchase transport days setup to calculate the shipping date, it uses the address where the **Primary** option is set to *Yes* as the shipping point.

    > [!TIP]
    > - The vendor address is applied to the purchase order and used as the shipping point from purchase transport days.
    > - Th purchase transport days receiving point is second part for calculate shipping date. The delivery address is depending on the setup and can be defaulted from company, site, warehouse. Updating the site or warehouse for a purchase order header or line will trigger a recalculation of shipping date, since the transport days may be different based on different delivery address on site or warehouse.

### <a name="calendars"></a>Calendars part of ship and receipt date calculation

Three calendars comes into play as part of the calculation

- Purchase calendar - when vendor is open. For instance, you can place an order the whole week except weekends
- Vendor Ship calendar - when purchase order can be shipped from the vendor
- Warehouse calendar - when purchase order can be delivered in the site or warehouse

The Purchase and vendor ship calendars are taken into account when calculating the ship date where as the warehouse / item coverage group calendar is used when calculating the receipt date.

Example
Below table contains the three calendars that takes part of the calculation of purchase order request ship and receipt date.

In first scenario we have a product with a lead time of 5 days and purchase transport days of 2 days.

- Ship date is Saturday where vendor ship calendar is open after 5 days lead time
- Receipt date is Tuesday since first open warehouse calendar day after 2 transport days

|                    |Mon   |Tue   |Wed   |Thu   |Fri   |Sat   |Sun   |Mon   |Tue   |
|:-------------------|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|Purchase calendar   |Open  |Open  |Open |Open   |Open  |Open  |Open  |Open  |Open  |
|Vendor ship calendar|Open  |Closed|Closed|Closed|Open  |Open  |Open  |Open  |Open  |
|Warehouse calendar  |Open  |Open  |Open  |Open  |Closed|Closed|Closed|Closed|Open  |
|**Below is the calculated dates**|
|Order date          |**X** |      |      |      |      |**X** |      |      |      |
|Ship date           |      |      |      |      |      |      |      |      |      |
|Receipt date        |      |      |      |      |      |      |      |      |**X** |

Second scenario we adjust the product lead time to 3 days and purchase transport days of 2 days.

- Ship date is moved one day, since vendor ship calendar is closed on Thursday
- Receipt date is moved two days, since warehouse calendar is closed on Sunday and Monday


|                    |Mon   |Tue   |Wed   |Thu   |Fri   |Sat   |Sun   |Mon   |Tue   |
|:-------------------|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|Purchase calendar   |Open  |Open  |Open |Open   |Open  |Open  |Open  |Open  |Open  |
|Vendor ship calendar|Open  |Closed|Closed|Closed|Open  |Open  |Open  |Open  |Open  |
|Warehouse calendar  |Open  |Open  |Open  |Open  |Closed|Closed|Closed|Closed|Open  |
|**Below is the calculated dates**|
|Order date          |**X** |      |      |      |      |      |      |      |      |
|Ship date           |      |      |      |      |**X** |      |      |      |      |
|Receipt date        |      |      |      |      |      |      |      |      |**X** |

Find more details on [Calendars and master planning](supply-chain-calendars-master-planning.md).

#### Assign vendor ship calendars

For each vendor, you can specify a ship calendar that indicates the dates when the vendor can ship. For example, some vendors might be able to ship during all opening hours, whereas others can ship only on Mondays. You can define as many specific ship calendars as you require and then apply them to each vendor as appropriate.

If you have goods that must be expedited, and the relevant vendor makes an exception on their vendor ship calendar, you can change or remove the vendor ship calendar for the relevant purchase order lines.

For information about how to set up a ship calendar and define the available ship dates and times for it, see [Calendars and master planning](supply-chain-calendars-master-planning.md).

To assign a ship calendar to a vendor, follow these steps.

1. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**.
1. Open the vendor record that you want to assign a ship calendar to.
1. On the **Invoice and delivery** FastTab, in the **Ship calendar** field, select the [ship calendar](supply-chain-calendars-master-planning.md) that applies to the vendor.

## Date calculations and recalculations

This section describes how and when the system calculates and recalculates requested ship dates.

### Requested ship date

The requested ship date calculation considers lead time (lead time per vendor if it's set up on trade agreements), the mode of delivery, and the vendor ship calendar. The lead time is the time that the vendor takes to produce the item. It doesn't include transport days (from vendor to company).

You can configure how the system handles requested ship dates that are in the past. For more information, see the [Specify whether requested ship dates can be in the past](#parameters) section.

### Order date of planned purchase orders

When a master planning run indicates that a planned order is needed, the order date is calculated backwards from the requirement date. The calculation considers margins, lead time, and the purchase transport days setup. The requested ship date is calculated according to the same rules that are used for purchase orders. However, for planned orders, the requested ship date isn't saved as a field value or shown on the **Planned purchase order** details page.

The requested ship date is also calculated for manually created planned purchase orders.

### Recalculations for updated orders

When you edit a purchase order where the requested and/or confirmed ship date has already been calculated, the system does the following recalculations:

- If the **Requested ship date** value is changed, the **Requested receipt date** value is recalculated.
- If the **Requested receipt date** value is changed, the **Requested ship date** value is recalculated.
- If the **Confirmed ship date** value is changed, the **Confirmed receipt date** value is recalculated.
- If the **Confirmed receipt date** value is changed, the **Confirmed ship date** value is recalculated.
- If any of the following information is changed, the relevant ship and receipt dates are recalculated:

  - Address on the header
  - Mode of delivery (on the header or on a line)
  - Warehouse on a line

If you change the **Requested ship date** or **Confirmed ship date** value on the header of a purchase order, the system asks you whether the relevant ship and receipt dates should also be updated for each line.

## Scenario date calculation

In this section purchase order requested ship and receipt date calculation is described.

Prerequisites for these scenario are:

- The feature that's named *Supplier requested and confirmed shipment dates* must be turned on in [Feature management](../../fin-ops-core/
- **Purchase transport days** is configured with receiving, shipping address and number of transport days. The address should match what is used for vendor and the purchase order line
- All calendars have all days open, if nothing else is specified.
- The **Procurement and sourcing parameters** field **Requested ship date in the past** is set to **None**

### Create purchase order

In this scenario we are using 2 purchase transport days from vendor shipping address to site/warehouse receiving address. Dates are calculated forward, requested ship date plus purchase transport days will result in and requested receipt date.

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. Create a new purchase order, on the Action Pane, select **New**.
1. On the **Vendor** FastTab, enter a value in the **Vendor account** field
1. Click **OK** to create the purchase order
1. On the **Purchase order lines** FastTab, enter a value in the **Item number** field and **Site / Warehouse** fields if required
1. On the **Line details** FastTab, select **Delivery** FastTab

The expected purchase order line requested dates should be :

- Requested ship date is set to current date initialized from the purchase order header requested ship date.
- Requested receipt date will be calculated to 2 purchase transport days ahead from the purchase order requested ship date.

If the product given on the purchase orde line has lead time then requested ship date will be purchase order date plus product lead time.

Updating the requested ship or receipt date will trigger date re-calculation. Update requested ship date will do a forward calculation of the requested receipt date, and updates to requested receipt date will do backward calculation of the requested ship date. Important availabilty of the vendor ship calendar and warehouse calendar has impact on the date calculation, see the [Calendars part of ship and receipt date calculation](#calendars) section.

### Create purchase order with dates in the past

In this scenario we use different configuration for the parameter [Specify whether requested ship dates can be in the past](#parameters)

Default value for the **Requested ship date in the past** parameter field is *None* – Always allow requested ship dates to be in the past, without showing a warning.

Date calculation will be different when we have dates in the past using the parameter value *Disallow with warning* – Always find the next earliest ship date that's after the current date, and show a warning message to users when this situation occurs.

Continue using 2 purchase transport days from vendor shipping address to site/warehouse receiving address

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. Create a new purchase order, on the Action Pane, select **New**.
1. On the **Vendor** FastTab, enter a value in the **Vendor account** field
1. Click **OK** to create the purchase order
1. On the **Purchase order lines** FastTab, enter a value in the **Item number** field and **Site / Warehouse** fields if required
1. On the **Line details** FastTab, select **Delivery** FastTab
1. Enter new date value in the past for the **Requested receipt date** field. E.g. Use **Requested ship date** as the new value.

Warning will be show *The requested ship date 1/1/2024 is not valid because it is before today. Earliest possible requested ship date is 1/9/2024 with requested receipt date 1/11/2024.* and date re-calculation done, setting the dates back to valid dates in the future.

Setting requested ship or receipt date in the past will also result in warning e.g. *The requested ship date 1/8/2024 is not valid because it is before today.* not allowing the date to the saved.

### Create purchase order from sales order

In this scenario we are using 2 purchase transport days from vendor shipping address to site/warehouse receiving address.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Create a new sales order, on the Action Pane, select **New**.
1. On the **Customer** FastTab, enter a value in the **Customer account** field
1. Click **OK** to create the sales order
1. On the **Sales order lines** FastTab, enter a value in the **Item number** field and **Site / Warehouse** fields if required
1. On the **Line details** FastTab, select **Delivery** FastTab
1. Enter **None** for the the **Delivery date control** field and date value for **Requested receipt date** field e.g. 5 days from current date.
1. On the **Sales order** action pane, select **Purchase order**
1. In the **Vendor account** field select a vendor (vendor address needs to match the shipping address on purchase transport days)
1. Select the **Include** checkbox, to include the sales for on the purchase order.
1. Click **OK** to create the purchase order
1. On the **General** action pane, select **Purchase order**
1. On the **Line details** FastTab, select **Delivery** FastTab

The expected purchase order line requested dates should be :

- Requested receipt date will be the set to sales order requested ship date
- Requested ship is calculated backward with number of purchase transport days to first available open date.

### Create Direct delivery from sales order

This scenario is similar to above create purchase order from sales, difference is that sales order request receipt date is set to purchase order requested receipt date and then calculating purchase transport backward to set requested ship date both on purchase and sales order.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Create a new sales order, on the Action Pane, select **New**.
1. On the **Customer** FastTab, enter a value in the **Customer account** field
1. Click **OK** to create the sales order
1. On the **Sales order lines** FastTab, enter a value in the **Item number** field and **Site / Warehouse** fields if required
1. On the **Line details** FastTab, select **Delivery** FastTab
1. Enter **None** for the the **Delivery date control** field and date value for **Requested receipt date** field e.g. 5 days from current date.
1. On the **Sales order** action pane, select **Direct delivery**
1. In the **Vendor account** field select a vendor (vendor address needs to match the shipping address on purchase transport days)
1. Select the **Include** checkbox, to include the sales for on the purchase order.
1. Click **OK** to create the purchase order
1. On the **General** action pane, select **Purchase order**
1. On the **Line details** FastTab, select **Delivery** FastTab

The expected sales and purchase order line requested dates should be :

- Requested receipt date will be the set to sales order requested receipt date
- Requested ship is calculated backward with number of purchase transport days to first available open date. The requested dates will be synchronized with sales order, so it the same requested dates on both sales and purchase order, because this is now marked as a direct delivery,

### Create Intercompany order

For intercompany order the requested ship and receipt dates needs to synchronized for both sales and purchase orders, taking into account the purchase transport days, lead time, delivery date control and calendars availability.

Prerequisites is that intercompany relation ship is setup between the customer and vendor used. Furthermore purchase transport days and products should be configured on all companies part of the intercompany relationship.

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. Create a new purchase order, on the Action Pane, select **New**.
1. On the **Vendor** FastTab, enter a value in the **Vendor account** field (Intercompany vendor)
1. Click **OK** to create the purchase order
1. On the **Purchase order lines** FastTab, enter a value in the **Item number** field and **Site / Warehouse** fields if required
1. On the **Line details** FastTab, select **Delivery** FastTab (Note the request ship and receipt date)

The expected purchase order line requested dates should be :

- Requested ship date is set to date initialized from the sales order taking delivery date control into consideration as part of the calculation.
- Requested receipt date will be calculated to 2 purchase transport days ahead from the purchase order requested ship date.

1. On the purchase order **Manage** action pane, select **Intercompany tracing** \> **Intercompany sales order**

The expected sales order line requested dates should match the dates on the purchase order line.

> [!TIP]
The sourcing order dictates how and if the purchase order transport days are calculated. 
>
> - If dates are updated on sales order then lead time and customer transport days takes presences and purchase order transports days are calculated.
> - If dates are update on purchase order, then purchase transport days and lead time are calculated and requested and confirmed dates are synchronized back to the sales order.

### Purchase agreement

In this scenario we create a purchase agreement, release purchase order setting request receipt date and see how the requested ship and receipt date are calculated. We still keep using 2 purchase transport days from vendor shipping address to site/warehouse receiving address.

1. Go to **Procurement and sourcing** \> **Purchase agreements** \> **Purchase agreements**.
1. Create a new purchase agreement, on the Action Pane, select **New**.
1. On the **Vendor** FastTab, enter a value in the **Vendor account** field
1. Click **OK** to create the purchase agreement
1. On the **Purchase agreement lines** FastTab, select **Add line**
1. Enter a value in the **Item number** field and **Site / Warehouse** fields if required
1. On the **Purchase agreement** action pane, select **Generate** \> **Confirmation**, click **OK**
1. On the **Purchase agreement** action pane, select **New** \> **Release order**
1. For the line enter value for the **Purchase quantity** field. (Note or set a different value in the **Requested receipt date** value)
1. Click **Create** to create the purchase order (Note the purchase order number from the info log message)
1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. Select the purchase order noted from above.

The expected purchase order line requested dates should be :

- Requested receipt date will be the value we did set when release order.
- Requested ship date is calculated backward 2 purchase transport days from the purchase order requested receipt date.

### Purchase requisition

Scenario describes creating purchase requisition, release of the order and the result of the requested ship and receipt date calculation.

1. Go to **Procurement and sourcing** \> **Purchase requisitions** \> **All purchase requisitions**.
1. Create a new purchase requisition, on the Action Pane, select **New**.
1. Enter a value in the **Name** field
1. On the **Purchase requisition lines** FastTab, select **Add line**
1. Enter a value in the **Item number** field (**Quantity**, **Unit**, **Site/Warehouse**' fields might be required)

The expected purchase requisition line requested date should be :

- Requested date from header plus 2 purchase transport days calcualted forward.

Generate purchase order for purchase requisition through the workflow **Submit requisition for approval**, will result in purchase order with following requested dates:

- Requested receipt date will be the set to the value **Requested date** from purchase requisistion
- Requested ship date is calculated backward 2 purchase transport days from the purchase order requested receipt date.

### Purchase request for quotation

Scenario describes creating purchase request for quotation, acceptance of RFQ reply and the result of the requested ship and receipt date calculation on the purchase order.

1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**.
1. On the **Request for quotation** FastTab, enable the **Purchaser can edit vendors bid** field

1. Go to **Procurement and sourcing** \> **Requests for quotations** \> **All requests for quotations requisitions**.
1. Create a new purchase requisition, on the Action Pane, select **New**.
1. Enter value for any required fields
1. Click **OK** to create the purchase agreement
1. Enter a value in the **Item number** field and **Site / Warehouse** fields if required
1. Select the **Header** FastTab
1. On the **Vendor** FastTab, enter a value in the **Vendor account** field
1. On the **Quotation** action pane, select **Process** \> **Send**, click **OK**
1. On the **Quotation** action pane, select **Replies** \> **Manage replies**
1. On the **Edit** action pane, select **Edit RFQ reply**
1. On the action pane, select **Submit**
1. On the **Reply** action pane, select **Process** \> **Accept**
1. Click **OK** to create the purchase order
1. On the **Genreral** action pane, select **Othe3r information** \> **Purchase order**

- Requested receipt date will be the set to the value **Requested receipt date** from request for quotation
- Requested ship date is calculated backward 2 purchase transport days from the purchase order requested receipt date.
