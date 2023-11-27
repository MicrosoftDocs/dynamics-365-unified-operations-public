---
title: Calculate requested ship dates for purchase orders (preview)
description: This topic describes how the system calculates requested ship dates for purchase orders and how to set up this calculation.
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

<!-- KFM: 

The name "Supplier requested and confirmed dates" makes it sound like the supplier is both requesting and confirming the dates. This topic seems mostly to be about calculating the ship dates (not other kinds of dates) for planned orders. It doesn't say whether that date is ever confirmed, but if so, we should mention/describe this in the text. I think maybe we should call this "Calculate requested ship dates for purchase orders". 

I think suppliers and vendors are always the same thing. Let's pick just one term for them (probably vendors).

This seems to apply both to purchase orders and planned orders. Does it make sense to list it twice in the TOC?

-->

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

<!--KFM: Confirm preview date and add to appropriate What's new -->

If you have vendors without specific delivery terms (such as delivery duty paid, delivery at place, or delivery at place unloaded) you must tell the vendor when they should ship <!-- KFM: Not clear. Please clarify or maybe remove.-->.

Purchase orders in Dynamics 365 Supply Chain Management can include both a *requested receipt date*, which specifies when the order should be received at your company's location, and a *requested ship date*, which specifies the date the vendor should ship from their location. The system calculates requested ship dates based on the requested receipt date, lead time, transportation days setup, vendor calendar, and other settings. The transportation days setup lets you define the number of days needed to transport items between various pairs of addresses. *Vendor ship calendars* define the days on which each vendor can ship.

When master planning suggests a date for placing a planned order, it also considers the transportation days setup to help make sure the goods will arrive on time.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To calculate requested ship dates, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Supplier requested and confirmed shipment dates* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must be using Planning Optimization, not the [deprecated master planning engine](deprecated-master-planning-overview.md).

## Requested and confirmed receipt dates on purchase orders

As of Supply Chain Management 10.0.38, the following date fields on purchase orders have been renamed to better align with similar date fields on sales orders, and to make it clear that these dates indicate when the items are to be *received* at your location, not when they are *sent* from the vendor's location:

- **Requested delivery date** is now labeled **Requested receipt date**.
- **Confirmed delivery date** is now labeled **Confirmed receipt date**.

## Requested ship dates in master planning

When a master planning run indicates that a planned order is needed, the order date is calculated backwards from the requirement date and takes into into account margins, lead time, and **Purchase transport days** setup. The requested ship date is calculated following the same rules as for purchase orders. However, the requested ship date isn't shown on the **Planned purchase order** details page.

## Choose whether to allow requested ship dates to be in the past

Sometimes, as a result of your requested receipt date, plus the lead time, transportation days, vendor calendar, and other settings, the system might calculate a requested ship date that is in the past. You can choose how the system should handle this situation by following these steps:

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. Open the **Delivery** tab.
1. Set **Requested ship date in the past** to one of the following values:
    - *None* – Always allow requested ship dates to be in the past without showing a warning.
    - *Allow with warning* – Allow requested ship dates to be in the past but show a warning message to users when they occur.
    - *Disallow with warning* – Always recalculate the requested ship date based on today's date and show a warning message to users when this occurs. <!-- KFM: Not clear. Please clarify.-->

## Set up purchase transport days

Follow these steps to define the number of days needed to transfer goods between various addresses:

1. Go to **Procurement and sourcing \> Setup \> Distribution \> Purchase transport days**.
1. Do one of the following steps:
    - If you're looking for an existing record, use the filters at the top of the grid to find it. To edit the found record, select the link in the **Shipping country/region** column. To delete a selected record, select **Delete** on the Action Pane.
    - If you're creating a new record, on the Action Pane, select **New**.
1. The details page for your new or selected record opens. Use the settings on the **General** tab to define the shipping address, receiving address, and the number of days needed to transport goods between them. For more information about a field, hover your mouse pointer over the field label to open a tooltip. Here are a few tips for filling out the fields:
    - A convenient way to fill out an address is to start by entering the **Shipping ZIP/postal code**. Often, then system can automatically fill out the rest of the address for you based on this.
    - When calculating the ship date, the system will use the most specific purchase transport days record it can find. For example, suppose you have just two purchase transport days records: one for Spain to USA of 30 days and another for Madrid to New York of 20 days. In this case, a purchase order shipping from Madrid to New York would use 20 days, while an order from Valencia to New York would use 30 days. <!-- KFM: Please confirm this; the original said the opposite. -->
    - If you need to specify the transport from a certain vendor to one of your warehouses, you must include the address of your warehouse. <!-- KFM: Not clear. Please clarify. -->
    - There is not a specific address for a vendor, a vendor can have many addresses <!-- KFM: How do these work? What if there is more than one? -->
1. On the **Transport days per mode of delivery** tab ... <!-- KFM: What do we do here? How does this work? How do these settings interact with the overall Transport days setting? -->

## Vendor settings for calculating requested ship dates

To calculate requested ship dates, you must set up each vendor with vendor addresses. To help make the calculation even more accurate, you can also set up vendor shipping calendars that define on which specific days each vendor can ship.

### Set up vendor addresses

To set up addresses for a vendor, go to **Procurement and sourcing \> Vendors \> All vendors**, open the vendor record that you want to work with, and use the settings on the **Addresses** FastTab to add and remove addresses as needed.

<!-- KFM: How do we handle vendors with multiple addresses? How do we know which address applies for each order? What if the vendor office (contact address) is in a different city than the warehouse they ship from? -->

### Assign vendor shipping calendars

For each vendor, you can specify a ship calendar that indicates the dates on which that vendor is able to ship. For example, some vendors might be able to ship during all opening hours, while others might only ship on Mondays. You can define as many specific ship calendars as you need and then apply them to each vendor as appropriate. If you have goods that need to be expedited, and the relevant vendor makes an exception on their vendor ship calendar, you can accommodate this by changing or removing the vendor ship calendar for the relevant purchase order lines.

For details about how to set up a shipping calendar and define the available ship dates and times for it, see [Calendars and master planning](supply-chain-calendars-master-planning.md).

To assign a calendar to a vendor, follow these steps:

1. Go to **Procurement and sourcing \> Vendors \> All vendors**.
1. Open the vendor record that you want to assign a calendar to.
1. Expand the **Invoice and delivery** FastTab.
1. In the **Ship Calendar** field, select the [ship calendar](supply-chain-calendars-master-planning.md) that applies to the vendor. <!-- KFM: We should describe how this setting interacts with the **Purchase calendar** setting that is also available on this page. What if just one is defined? -->

<!-- KFM: 

Maybe we need a section called something like "Work with calculated ship dates for purchase orders". Here we can describe:
o	Which send address will be used for each order/line when calculating send date.
o	Which destination address will be used for each order/ line when calculating send date.
o	How to change vendor calendar for an order line.
o	How to manually override the calculated requested ship date (is this possible? what conditions apply?)
o	How editing the dates in the header affects the lines.
o	What changes will trigger a recalculation of shipping date. (Maybe)

Maybe we need a section that mentions that requested ship dates can be confirmed by the vendor, how this happens, and what effect it has.

-->

## Date calculations and recalculations

<!-- KFM: This section looks like specs, not docs. I'm not sure users need this. We should either make this more use-oriented or remove it. I think we can remove it. Some of this info could be incorporated into the proposed section above. -->

### Requested ship date

Requested ship date is calculated taking into account lead time (lead time per vendor if set up on trade agreements), mode of delivery, and vendor shipping calendar.

It is expected that the lead time is the time it takes for the vendor to produce the item. It does NOT include the transport days (from vendor to company).

Requested ship date must be calculated backwards from the requested receipt date, transport days and finding the previous open date on the vendor ship calendar.

The requested ship date must be today or later. If prior to today, then requested ship receipt dates must be recalculated according to the first feasible ship date. <!-- KFM: Don't we have a setting for how to handle this? -->

Confirmed dates can be in the past.

### Requested receipt date

This field currently is calculated according to the lead time of the item. It must be modified so that it also takes into account the transport days (lead time + transport days)

### Order date on planned purchase orders

Order date on planned purchase order must also be modified so that when calculating backwards from requirement date it makes sure that a part of the lead time, the new transport days are taking into account, and that the shipping date (not saved as a field on the planned purchaser order but should be taken into account in the calculation) must be an open day in the vendor calendar.

### Updates between the dates

- When Requested ship date is changed, Requested receipt date must be recalculated.
- When Requested receipt date is changed, Requested ship date must be recalculated.
- When Confirmed ship date is changed, Confirmed receipt date must be recalculated.
- When Confirmed receipt date is changed, Confirmed ship date must be recalculated.

If

- Address is changed on the header
- Or mode of delivery (on the header or on the lines)
- Or warehouse is changed on the line

Then, dates must be recalculated

### Updates between header and lines

If "Requested ship date" or "Confirmed ship date" are updated on the header, the dialog will be prompted to ask the user if these dates on the lines should be updated.

### Manual creation of planned purchase orders

Requested ship date will also be calculated

### On purchase order confirmation

Ship date will also be added <!--KFM: Do you mean confirmed ship date?  -->

Note the calculation will not be applicable to:

- receipt journal and invoice journal.
- RFQ reply
- receipt journal, invoice journal, Vendor collaboration
- History

