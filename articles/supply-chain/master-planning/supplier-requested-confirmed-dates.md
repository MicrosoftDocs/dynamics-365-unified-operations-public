---
title: Calculate requested ship dates for purchase orders
description: Learn how the system calculates requested ship dates for purchase orders, including prerquisites and an outline on receipt dates on purchase orders.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 11/16/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: VendCustTransportPoint2Point, SrmParameters, VendTable
---

# Calculate requested ship dates for purchase orders

[!include [banner](../includes/banner.md)]

Purchase orders in Microsoft Dynamics 365 Supply Chain Management can include both a *requested receipt date*, which specifies when the order should be received at your company's location, and a *requested ship date*, which specifies when the vendor should ship from their location. The system calculates requested ship dates based on the requested receipt date, lead time, the transport days setup, the vendor ship calendar, and other settings. The transport days setup lets you define the number of days that are required to transport items between pairs of addresses. Vendor ship calendars define the days when each vendor can ship.

If any of your vendors don't have specific delivery terms (such as delivery duty paid, delivery at place, or delivery at place unloaded), you must tell them when they should ship.

When master planning suggests a date for placing a planned order, it also considers the transport days setup. This approach helps ensure that the goods arrive on time.

## Prerequisites

To calculate requested shipment dates for purchase orders, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management version 10.0.38 or later.
- You must be using Planning Optimization, not the [deprecated master planning engine](deprecated-master-planning-overview.md).

Additional requirements apply based on which version of Supply Chain Management you are running, as described in the following subsections.

### Supply Chain Management versions 10.0.38 or 10.0.39

If you are running Supply Chain Management version 10.0.38 or 10.0.39, the feature that's named *Supplier requested and confirmed shipment dates* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Supply Chain Management version 10.0.40 or later

Starting in version 10.0.40 (and later), the *Supplier requested and confirmed shipment dates* feature is no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Instead, the feature is always available and is controlled by a setting on the **Procurement and sourcing parameters** page. The setting is turned off by default for all legal entities unless you had previously turned on the *Supplier requested and confirmed shipment dates* feature in feature management (before upgrading to version 10.0.40 or later), in which case the setting will be turned on for all legal entities.

To turn on the feature, follow these steps:

1. Use the company picker to select the legal entity (company) where you want to calculate requested shipment dates for purchase orders.
1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**.
1. Open the **Delivery** tab.
1. Set **Supplier requested and confirmed shipment dates** to *Yes* to make the feature available to the current legal entity. Set to *No* to hide the feature for the current legal entity.
1. Repeat this procedure for each legal entity where you want to turn on (or turn off) the option.

> [!NOTE]
> If you use intercompany trade, then each of the legal entities involved must have this option turned on to allow requested shipment dates to be calculated for intercompany purchase orders.

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
    > - If the shipping address and receiving address have equal priority, the shipping address takes precedence.

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
> - The vendor address is applied to the purchase order and used as the shipping point for purchase transport days.
> - The receiving point for purchase transport days is the second factor that's used to calculate the shipping date. The delivery address depends on the setup, and a default value can be taken from the company, site, or warehouse. Any update to the site or warehouse for a purchase order header or line triggers a recalculation of the shipping date, because the new site or warehouse might have a different delivery address.

### <a name="calendars"></a>How calendars affect ship and receipt date calculations

The following calendars are relevant for ship and receipt date calculations:

- **Purchase calendar** – This calendar defines when a vendor is open. For example, a vendor might accept orders on workdays but not weekends.
- **Vendor ship calendar** – This calendar defines when purchase orders can be shipped from the vendor.
- **Warehouse calendar** – This calendar defines when purchase orders can be received at the site or warehouse.

The purchase and vendor ship calendars are considered when the ship date is calculated. The warehouse (item coverage group) calendar is used when the receipt date is calculated.

Learn more in [Calendars and master planning](supply-chain-calendars-master-planning.md).

The following examples show how calendars affect the calculation of requested ship and receipt dates for purchase orders.

#### Calculation example 1

This example shows how requested ship and receipt dates are calculated for a product that has five days of lead time and two purchase transport days.

The following table shows the calendars that apply.

| Calendar | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|---|---|---|---|---|---|---|---|---|---|
| Purchase calendar | Open | Open | Open | Open | Open | Open | Open | Open | Open |
| Vendor ship calendar | Open | Closed | Closed | Closed | Open | Open | Open | Open | Open |
| Warehouse calendar | Open | Open | Open | Open | Closed | Closed | Closed | Closed | Open |

The following table shows the calculated dates.

| Date type | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|---|---|---|---|---|---|---|---|---|---|
| Order date | X | | | | | | | | |
| Ship date | | | | | | X | | | |
| Receipt date | | | | | | | | | X |

The calculation results are based on the following information:

- The ship date is Saturday, which is the first open day that's available in the vendor ship calendar after the five days of lead time.
- The receipt date is Tuesday, which is the first open day that's available in the warehouse calendar after the two transport days.

#### Calculation example 2

This example shows how requested ship and receipt dates are calculated for a product that has three days of lead time and two purchase transport days.

The following table shows the calendars that apply.

| Calendar | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|---|---|---|---|---|---|---|---|---|---|
| Purchase calendar | Open | Open | Open | Open | Open | Open | Open | Open | Open |
| Vendor ship calendar | Open | Closed | Closed | Closed | Open | Open | Open | Open | Open |
| Warehouse calendar | Open | Open | Open | Open | Closed | Closed | Closed | Closed | Open |

The following table shows the calculated dates.

| Calendar | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Mon | Tue |
|---|---|---|---|---|---|---|---|---|---|
| Order date | X | | | | | | | | |
| Ship date | | | | | X | | | | |
| Receipt date | | | | | | | | | X |

Compared to the previous example, the results are calculated in the following way:

- The ship date is moved one day, because the vendor ship calendar shows that the vendor is closed on Thursday.
- The receipt date is moved two days, because the warehouse calendar shows that the warehouse is closed on Sunday and Monday.

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

When a master planning run indicates that a planned order is needed, the order date is calculated backward from the requirement date. The calculation considers margins, lead time, and the purchase transport days setup. The requested ship date is calculated according to the same rules that are used for purchase orders. However, for planned orders, the requested ship date isn't saved as a field value or shown on the **Planned purchase order** details page.

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

## Example date calculation scenarios

This section provides examples that show how requested ship and receipt dates for purchase orders are calculated in various scenarios.

### Example scenario prerequisites

These scenarios have the following prerequisites:

- You system must meet all the feature prerequisites that are listed in the [Prerequisites](#prerequisites) section of this article.
- The **Purchase transport days** page must be configured with at least one receiving address, shipping address, and number of transport days. The addresses must match the vendors and receiving warehouses that you use for these scenarios.
- Unless otherwise specified, all calendars must have all days open.
- On the **Procurement and sourcing parameters** page, on the **Delivery** tab, the **Requested ship date in the past** field must be set to *None*.

### Example scenario 1: Standard purchase order

In this scenario, there are two purchase transport days from the vendor shipping address to the site/warehouse receiving address. Dates are calculated forward, and the purchase transport days are added to the requested ship date to determine the requested receipt date.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor shipping address that you plan to order from to the warehouse receiving address where you plan to receive the order. Set the **Transport days** field to *2* for this record.
1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. On the Action Pane, select **New** to create a purchase order.
1. On the **Vendor** FastTab, set the **Vendor account** field to the vendor whose shipping address you set up on the **Purchase transport days** page. Then select **OK** to create and open the purchase order.
1. On the **Purchase order lines** FastTab, in the **Item number** field, select an item. Then set the **Site** and **Warehouse** fields to the warehouse that you set up a receiving address for on the **Purchase transport days** page.
1. On the **Line details** FastTab, on the **Delivery** tab, you should see the following values:

    - **Requested ship date** – The value is the current date (unless you specified another date for the order header).
    - **Requested receipt date** – The value is a date that's two days later than the **Requested ship date** value for the purchase order. The system calculates this date based on your setup on the **Purchase transport days** page. The following settings can also affect the calculation:

        - If the product that's ordered has lead time, the system adds that lead time to the transport time when it calculates the receipt date. (Therefore, the formula is *Requested ship date* = *Requested ship date* &plus; *Product lead time*.)
        - The vendor ship calendar and warehouse calendar can also affect the date calculation by allowing for closing times at one or both locations. (For more information, see the [How calendars affect ship and receipt date calculations](#calendars) section.)

    Any update to the **Requested ship date** or **Requested receipt date** value causes the system to recalculate the dates. An update to the **Requested ship date** value triggers a forward calculation of the **Requested receipt date** value, and an update to the **Requested receipt date** value triggers a backward calculation of the **Requested ship date** value.

### Example scenario 2: Purchase order with dates in the past

This scenario shows how the system handles requested ship dates that are in the past, based on the **Requested ship date in the past** setting. (For more information, see the [Specify whether requested ship dates can be in the past](#parameters) section.)

The default value of the **Requested ship date in the past** field is *None*. In this case, requested ship dates in the past are always allowed, and no warning is shown. This scenario shows what happens if you change the value to *Disallow with warning*. In this case, a warning message is always shown if requested ship dates are in the past. The system then finds the next earliest ship date that's after the current date.

1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**.
1. On the **Delivery** tab, set the **Requested ship date in the past** field to *Disallow with warning*. Then select **Save**.
1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor shipping address that you plan to order from to the warehouse receiving address where you plan to receive the order. Set the **Transport days** field to *2* for this record.
1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. On the Action Pane, select **New** to create a purchase order.
1. On the **Vendor** FastTab, set the **Vendor account** field to the vendor whose shipping address you set up on the **Purchase transport days** page. Then select **OK** to create and open the purchase order.
1. On the **Purchase order lines** FastTab, in the **Item number** field, select an item. Then set the **Site** and **Warehouse** fields to the warehouse that you set up a receiving address for on the **Purchase transport days** page.
1. On the **Line details** FastTab, on the **Delivery** tab, set the **Requested receipt date** field to a date that doesn't allow for enough time for transport. (For example, select today's date.)

    The system shows a warning message such as "The requested ship date 1/18/2024 is not valid because it is before today. Earliest possible requested ship date is 1/22/2024 with requested receipt date 1/26/2024." The requested date fields are updated to match the warning message.

    If you try to directly enter a requested ship or receipt date that's in the past, you receive a warning that doesn't include any suggested dates (for example, "The requested ship date 1/8/2024 is not valid because it is before today"). In this case, you can't save the order until you select a valid date.

### Example scenario 3: Purchase order created from a sales order

In this scenario, you create a purchase order from a related sales order and observe how the requested ship and receipt dates are calculated for both orders.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor shipping address that you plan to order from to the warehouse receiving address where you plan to receive the order. Set the **Transport days** field to *2* for this record.
1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New** to create a sales order.
1. On the **Customer** FastTab, set the **Customer account** field to any customer account (it doesn't matter which one). Then select **OK** to create and open the sales order.
1. On the **Sales order lines** FastTab, in the **Item number** field, select an item. Then set the **Site** and **Warehouse** fields to the warehouse that you set up a receiving address for on the **Purchase transport days** page.
1. On the **Line details** FastTab, on the **Delivery** tab, set the **Delivery date control** field to *None*.
1. Set both the **Requested ship date** field and the **Requested receipt date** field to a date that's one week from now.
1. On the Action Pane, on the **Sales order** tab, in the **New** group, select **Purchase order**.
1. On the **Lines** FastTab, you should see a line that matches the line from your sales order. For this line, set the **Vendor account** field to the vendor whose shipping address you set up on the **Purchase transport days** page.
1. Select the **Include** checkbox for the line.
1. Select **OK** to create the purchase order and return to your sales order.
1. On the Action Pane, on the **General** tab, in the **Related information** group, select **Purchase order**.
1. The related purchase order is opened. On the **Line details** FastTab, on the **Delivery** tab, you should see the following values:

    - **Requested receipt date** – The value matches the sales order's requested ship date.
    - **Requested ship date** – The value is calculated backward from the receipt date, based on the number of purchase transport days, to the first available open date.

### Example scenario 4: Direct delivery created from a sales order

This scenario is similar to the previous one, but you create a [direct delivery order](../sales-marketing/direct-deliveries.md) from a sales order. Because you're using direct delivery for this scenario, the shipment never arrives at your warehouse. Therefore, transport time is calculated based only on the *vendor's shipping address* and the *customer's receiving address*.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor shipping address that you plan to order from to the receiving address of the *customer* that you plan to ship to. Set the **Transport days** field to *2* for this record.
1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New** to create a sales order.
1. On the **Customer** FastTab, set the **Customer account** field to the customer whose receiving address you set up on the **Purchase transport days** page. Then select **OK** to create and open the sales order.
1. On the **Sales order lines** FastTab, in the **Item number** field, select an item. Then set the **Site** and **Warehouse** fields if they're required. However, these fields don't affect the delivery time calculation, because you're using direct delivery.
1. On the **Line details** FastTab, on the **Delivery** tab, set the **Delivery date control** field to *None*.
1. Set both the **Requested ship date** field and the **Requested receipt date** field to a date that's one week from now.
1. On the Action Pane, on the **Sales order** tab, in the **New** group, select **Direct delivery**.
1. On the **Lines** FastTab, you should see a line that matches the line from your sales order. For this line, set the **Vendor account** field to the vendor whose shipping address that you set up on the **Purchase transport days** page.
1. Select the **Include** checkbox for the line.
1. Select **OK** to create the purchase order and return to your sales order.
1. On the **Line details** FastTab, on the **Delivery** tab, you should see the following values:

    - **Requested receipt date** – The value is the requested ship date that you entered earlier.
    - **Requested ship date** – The value is calculated backward from the receipt date, based on the number of purchase transport days, to the first available open date.

1. On the Action Pane, on the **General** tab, in the **Related information** group, select **Purchase order**.
1. The related purchase order is opened. On the **Line details** FastTab, on the **Delivery** tab, notice that the **Requested receipt date** and **Requested ship date** values match the values of the sales order. These dates are synced because this order is a direct delivery order.

### Example scenario 5: Intercompany order

For intercompany orders, the requested ship and receipt dates must be synced for both sales orders and purchase orders. The purchase transport days, lead time, delivery date control, and calendar availability must also be considered.

To complete this scenario, you must already have an intercompany relationship set up between the customer and vendor that you'll use.

1. Use the company picker to select the company that's purchasing an item. This company is the one where you must set up the purchase transport days and create the purchase order.
1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor warehouse to the customer warehouse that you're using for this scenario. Set the **Transport days** field to *2* for this record.
1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. On the Action Pane, select **New** to create a purchase order.
1. On the **Vendor** FastTab, set the **Vendor account** field to the intercompany vendor whose shipping address you set up on the **Purchase transport days** page. Then select **OK** to create and open the purchase order.
1. On the **Purchase order lines** FastTab, in the **Item number** field, select an item. Then set the **Site** and **Warehouse** fields to the warehouse that you set up a receiving address for on the **Purchase transport days** page.
1. On the **Line details** FastTab, on the **Delivery** tab, you should see the following values:

    - **Requested ship date** – The value is the current date (unless you specified another date for the order header).
    - **Requested receipt date** – The value is a date that's five days later than the **Requested ship date** value of the purchase order. The system calculated this date based on your purchase transport days setup.

1. On the Action Pane, on the **Manage** tab, in the **Intercompany tracing** group, select **Intercompany sales order**. The requested dates on the sales order line should match the dates that you saw on the purchase order line.

> [!TIP]
> The sourcing order determines whether and how the purchase order transport days are calculated.
>
> - If dates are updated on the sales order, lead time and customer transport days take precedence, and purchase order transport days are calculated. These dates are editable only when you source from the sales order.
> - If dates are updated on the purchase order, purchase transport days and lead time are calculated, and requested and confirmed dates are synced back to the sales order.

### Example scenario 6: Purchase agreement

This scenario shows how requested ship and receipt dates are calculated when you create a purchase order from a purchase agreement.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor shipping address that you plan to create a purchase agreement for to the warehouse receiving address where you plan to receive the order. Set the **Transport days** field to *2* for this record.
1. Go to **Procurement and sourcing** \> **Purchase agreements** \> **Purchase agreements**.
1. On the Action Pane, select **New** to create a purchase agreement.
1. On the **Vendor** FastTab, set the **Vendor account** field to the vendor whose shipping address you set up on the **Purchase transport days** page. Then select **OK** to create and open the purchase agreement.
1. On the **Purchase agreement lines** FastTab, select **Add line**.
1. In the **Item number** field, select an item. Then set the **Site** and **Warehouse** fields to the warehouse that you set up a receiving address for on the **Purchase transport days** page.
1. On the Action Pane, on the **Purchase agreement** tab, in the **Generate** group, select **Confirmation**.
1. In the **Confirm purchase agreement** dialog box, select **OK**.
1. On the Action Pane, on the **Purchase agreement** tab, in the **New** group, select **Release order**.
1. In the **Create release order** dialog box, in the **Purchase quantity** field for the line, enter a value. Then set the **Requested receipt date** field to one week from today.
1. Select **Create** to create the purchase order.
1. Make a note of the purchase order number that's shown in the message at the top of the page.
1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. Open the purchase order that you just created. Use the purchase order number that you made a note of to find it.
1. On the **Line details** FastTab, on the **Delivery** tab, you should see the following values:

    - **Requested receipt date** – The value is the date that you entered when you released the purchase order.
    - **Requested ship date** – The value is calculated backward from the receipt date, based on the number of purchase transport days, to the first available open date.

### Example scenario 7: Purchase requisition

This scenario shows how requested ship and receipt dates are calculated when you create a purchase order from a purchase requisition.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor shipping address that you plan to create a purchase requisition for to the warehouse receiving address where you plan to receive the order. Set the **Transport days** field to *2* for this record.
1. Go to **Procurement and sourcing** \> **Purchase requisitions** \> **All purchase requisitions**.
1. On the Action Pane, select **New** to create a purchase requisition.
1. In the **Name** field, enter a name for the requisition. Then select **OK** to create and open the purchase requisition.
1. On the **Purchase requisition lines** FastTab, on the toolbar, select **Add line**.
1. In the **Item number** field, enter a value. Then, in the **Quantity** field, specify a quantity.
1. On the **Line details** FastTab, on the **Inventory dimensions** tab, set the **Site** and **Warehouse** fields to the warehouse that you set up a receiving address for on the **Purchase transport days** page.
1. On the Action Pane, select **Workflow** to open a dropdown dialog box. Select **Submit** to open a dialog box where you can enter a comment. Then select **Submit** in this dialog box to submit the requisition for approval.
1. Generate a purchase order for the purchase requisition through the **Submit requisition for approval** workflow. The resulting purchase order should have the following requested dates:

    - **Requested receipt date** – The value is the **Requested date** value from the purchase requisition.
    - **Requested ship date** – The value is calculated backward two purchase transport days from the requested receipt date of the purchase order.

### Example scenario 8: Purchase request for quotation

This scenario shows how requested ship and receipt dates are calculated when you create a purchase order from a request for quotation (RFQ) reply.

1. Go to **Procurement and sourcing** \> **Setup** \> **Distribution** \> **Purchase transport days**.
1. Make sure that you have a record for delivery from the vendor shipping address that you plan to create a purchase requisition for to the warehouse receiving address where you plan to receive the order. Set the **Transport days** field to *2* for this record.
1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**.
1. On the **Request for quotation** tab, set the **Purchaser can edit vendors bid** option to *Yes*.
1. Go to **Procurement and sourcing** \> **Requests for quotations** \> **All requests for quotations**.
1. On the Action Pane, select **New** to create an RFQ.
1. Set the **Requested receipt date** field to one week from today. Then enter values in any other required fields, and select **OK** to create the RFQ.
1. On the **Request for quotation lines** FastTab, in the **Item number** field, select an item. Then set the **Site** and **Warehouse** fields to the warehouse that you set up a receiving address for on the **Purchase transport days** page.
1. On the **Header** tab, on the **Vendor** FastTab, set the **Vendor account** field to the vendor whose shipping address you set up on the **Purchase transport days** page.
1. On the Action Pane, select **Save**.
1. On the Action Pane, on the **Quotation** tab, in the **Process** group, select **Send**.
1. In the **Sending request for quotation** dialog box, select **OK**.
1. On the Action Pane, on the **Quotation** tab, in the **Replies** group, select **Manage replies**.
1. On the Action Pane, select **Edit** \> **Edit RFQ reply**.
1. On the Action Pane, select **Submit**.
1. In the **Submit** dialog box, select **OK**.
1. On the Action Pane, on the **Reply** tab, in the **Process** group, select **Accept**.
1. In the **Accepting request for quotation** dialog box, select **OK** to create the purchase order.
1. On the Action Pane, on the **General** tab, in the **Other information** group, select **Purchase order**.
1. Open the new purchase order.
1. On the **Line details** FastTab, on the **Delivery** tab, you should see the following values:

    - **Requested receipt date** – The value matches the **Requested receipt date** value from the RFQ.
    - **Requested ship date** – The value is calculated backward from the requested receipt date, based on the purchase transport days setup.
