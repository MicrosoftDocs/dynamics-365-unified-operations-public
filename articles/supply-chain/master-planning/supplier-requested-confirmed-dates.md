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
>
> - The vendor address is applied to the purchase order and used as the shipping point for purchase transport days.
> - The purchase transport days receiving point is the second factor used to calculate the shipping date. The delivery address depends on the setup and can be defaulted from the company, site, or warehouse. Updating the site or warehouse for a purchase order header or line triggers a recalculation of the shipping date because the new site or warehouse could have a different delivery address.

### <a name="calendars"></a>How calendars affect ship and receipt date calculations

The following calendars are relevant for ship and receipt date calculations:

- **Purchase calendar** – Defines when a vendor is open. For example, a vendor may accept orders on work days but not weekends.
- **Vendor ship calendar** – Defines when purchase orders can be shipped from the vendor.
- **Warehouse calendar** - Defines when a purchase order can be received at the site or warehouse.

The purchase and vendor-ship calendars are considered when calculating the ship date, while the warehouse (item coverage group) calendar is used when calculating the receipt date.

For more information, see [Calendars and master planning](supply-chain-calendars-master-planning.md).

The following examples show how calendars affect the calculation of purchase order request ship and receipt dates.

#### Calculation example 1

This example shows how requested ship and receipt dates are calculated for a product with a five-day lead time and two purchase transport days.

The following table shows the calendars that apply.

| Calendar | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|--|--|--|--|--|--|--|--|--|--|
| Purchase calendar | Open | Open | Open | Open | Open | Open | Open | Open | Open |
| Vendor ship calendar | Open | Closed | Closed | Closed | Open | Open | Open | Open | Open |
| Warehouse calendar | Open | Open | Open | Open | Closed | Closed | Closed | Closed | Open |

The following table shows the calculated dates.

| Date type | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|--|--|--|--|--|--|--|--|--|--|
| Order date | X |  |  |  |  |  |  |  |  |
| Ship date |  |  |  |  |  | X |  |  |  |
| Receipt date |  |  |  |  |  |  |  |  | X |

The calculation results are based on the following information:

- The ship date is Saturday, which is when the vendor ship calendar is open after allowing five days lead time.
- The receipt date is Tuesday because that's the first open warehouse calendar day available after allowing two transport days.

#### Calculation example 2

This example shows how request ship and receipt dates are calculated for a product with a three-day lead time and two purchase transport days.

The following table shows the calendars that apply.

| Calendar | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|--|--|--|--|--|--|--|--|--|--|
| Purchase calendar | Open | Open | Open | Open | Open | Open | Open | Open | Open |
| Vendor ship calendar | Open | Closed | Closed | Closed | Open | Open | Open | Open | Open |
| Warehouse calendar | Open | Open | Open | Open | Closed | Closed | Closed | Closed | Open |

The following table shows the calculated dates.
| Calendar | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|--|--|--|--|--|--|--|--|--|--|
| Order date | X |  |  |  |  |  |  |  |  |
| Ship date |  |  |  |  | X |  |  |  |  |
| Receipt date |  |  |  |  |  |  |  |  | X |

Compared to the previous example, the calculation results are as follows:

- The ship date is moved one day because the vendor ship calendar shows the vendor is closed on Thursday
- The receipt date is moved two days because warehouse calendar shows the warehouse is closed on Sunday and Monday

### Assign vendor ship calendars

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

## Example date-calculation scenarios

In this section provides examples of how purchase order requested ship and receipt dates are calculated in various scenarios.

### Example scenario prerequisites

Prerequisites for these scenario are:

- The feature that's named *Supplier requested and confirmed shipment dates* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- The **Purchase transport days** page must be configured with receiving address, shipping address, and number of transport days. The addresses must match the vendors and the purchase order lines specified in these scenarios.
- All calendars have all days open unless otherwise specified.
- On the **Procurement and sourcing parameters** page, on the **Delivery** tab, the **Requested ship date in the past** field must be set to *None*.

### Example scenario 1: Create purchase order

In this scenario we are using 2 purchase transport days from vendor shipping address to site/warehouse receiving address. Dates are calculated forward, requested ship date plus purchase transport days will result in and requested receipt date.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**. Make sure you have a record for delivering from the vendor shipping address you plan to order from to the warehouse receiving address you plan to receive to. Set **Transport days** to *2* for this record.
1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. On the Action Pane, select **New** to create a new purchase order.
1. On the **Vendor** FastTab, set **Vendor account** to the vendors whose shipping address you set up on the **Purchase transport days** page. Select **OK** to create the purchase order.
1. On the **Purchase order lines** FastTab, select an item in the **Item number** field and set **Site** and **Warehouse** to the warehouse whose receiving address you set up on the **Purchase transport days** page.
1. On the **Line details** FastTab, select **Delivery** FastTab. Note the following values:

    - **Requested ship date** – Shows current date (unless you specified another date for the order header).
    - **Requested receipt date** – Shows a date that is two days later than the purchase order **Requested ship date**. The system calculated this date based on your **Purchase transport days** setup. The following settings can also affect the calculation:
        - If the product being ordered has a lead time, then the system will add that lead time to the transport time when calculating the receipt date (so that *requested ship date* = *requested ship date* &plus; *product lead time*).
        - The vendor ship calendar and warehouse calendar can also impact the date calculation to allow for closing times at one or both locations (see the [Calendars part of ship and receipt date calculation](#calendars)).

    Updating the **Requested ship date** or **Requested receipt date** causes the system to recalculate the dates. Updating the **Requested ship date** triggers a forward calculation of the **Requested receipt date**, and updating the **Requested receipt date** triggers a backward calculation of the **Requested ship date**.

### Example scenario 2: Create purchase order with dates in the past

This scenario shows how the system handles requested ship dates that are in the past based on your **Requested ship date in the past** setting (see also [Specify whether requested ship dates can be in the past](#parameters)).

The default value for **Requested ship date in the past** is *None*, which always allows requested ship dates to be in the past without showing a warning. This scenario shows what happens if you use a setting of *Disallow with warning*, which always shows a warning message when this situation occurs and then finds the next earliest ship date that's after the current date.

Continue using 2 purchase transport days from vendor shipping address to site/warehouse receiving address

1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**. On the **Delivery** tab, set  **Requested ship date in the past** to *Disallow with warning*. Then select **Save**.
1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**. Make sure you have a record for delivering from the vendor shipping address you plan to order from to the warehouse receiving address you plan to receive to. Set **Transport days** to *2* for this record.
1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. On the Action Pane, select **New** to create a new purchase order.
1. On the **Vendor** FastTab, set **Vendor account** to the vendors whose shipping address you set up on the **Purchase transport days** page. Select **OK** to create the purchase order.
1. On the **Purchase order lines** FastTab, select an item in the **Item number** field and set **Site** and **Warehouse** to the warehouse whose receiving address you set up on the **Purchase transport days** page.
1. On the **Line details** FastTab, select **Delivery** FastTab
1. Set **Requested receipt date** that doesn't allow enough time for transport (for example, today).
1. The system shows a warning message such as *The requested ship date 1/18/2024 is not valid because it is before today. Earliest possible requested ship date is 1/22/2024 with requested receipt date 1/26/2024.* The requested date fields are updated to match the warning message.

    If you try to set the requested ship or receipt date all in the past, you'll get a warning without any suggested dates (*The requested ship date 1/8/2024 is not valid because it is before today.*). In this case, you won't be allowed to save the order until you have selected a valid date.

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

### Create direct delivery from sales order

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

Prerequisites is that intercompany relationship is set up between the customer and vendor used. Furthermore purchase transport days and products should be configured on all companies part of the intercompany relationship.

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
> The sourcing order dictates how and if the purchase order transport days are calculated.
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

The expected purchase order line requested dates should be:

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

- Requested date from header plus 2 purchase transport days calculated forward.

Generate purchase order for purchase requisition through the workflow **Submit requisition for approval**, will result in purchase order with following requested dates:

- Requested receipt date will be the set to the value **Requested date** from purchase requisition
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
1. On the **General** action pane, select **Other information** \> **Purchase order**

- Requested receipt date will be the set to the value **Requested receipt date** from request for quotation
- Requested ship date is calculated backward 2 purchase transport days from the purchase order requested receipt date.
