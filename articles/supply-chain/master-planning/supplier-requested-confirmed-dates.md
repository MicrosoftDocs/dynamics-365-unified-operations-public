---
title: Calculate requested ship dates for purchase orders (preview)
description: This article describes how the system calculates requested ship dates for purchase orders and how to set up this calculation.
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

Purchase orders in Dynamics 365 Supply Chain Management can include both a *requested receipt date*, which specifies when the order should be received at your company's location, and a *requested ship date*, which specifies the date the vendor should ship from their location. The system calculates requested ship dates based on the requested receipt date, lead time, transportation days setup, vendor ship calendar, and other settings. The transportation days setup lets you define the number of days needed to transport items between various pairs of addresses. *Vendor ship calendars* define the days on which each vendor can ship.

If you have vendors without specific delivery terms (such as delivery duty paid, delivery at place, or delivery at place unloaded) you must tell the vendor when they should ship.

When master planning suggests a date for placing a planned order, it also considers the transportation days setup to help make sure the goods arrive on time.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To calculate requested ship dates, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Supplier requested and confirmed shipment dates* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must be using Planning Optimization, not the [deprecated master planning engine](deprecated-master-planning-overview.md).

## Requested and confirmed receipt dates on purchase orders

As of Supply Chain Management 10.0.38, the following date fields on purchase orders have been renamed to better align with similar date fields on sales orders, and to make it clear that these dates indicate when the items are to be *received* at your location, not when they're *sent* from the vendor's location:

- **Requested delivery date** is now labeled **Requested receipt date**.
- **Confirmed delivery date** is now labeled **Confirmed receipt date**.

## <a name="parameters"></a>Choose whether to allow requested ship dates to be in the past

Sometimes, as a result of your requested receipt date, plus the lead time, transportation days, vendor ship calendar, and other settings, the system might calculate a requested ship date that is in the past. You can choose how the system should handle this situation by following these steps:

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. Open the **Delivery** tab.
1. Set **Requested ship date in the past** to one of the following values:
    - *None* – Always allow requested ship dates to be in the past without showing a warning.
    - *Allow with warning* – Allow requested ship dates to be in the past but show a warning message to users when they occur.
    - *Disallow with warning* – Always find the next earliest ship date that is after today and show a warning message to users when this situation occurs.

## Set up purchase transport days

Follow these steps to define the number of days needed to transfer goods between various addresses:

1. Go to **Procurement and sourcing \> Setup \> Distribution \> Purchase transport days**.
1. Do one of the following steps:
    - If you're looking for an existing record, use the filters at the top of the grid to find it. To edit the found record, select the link in the **Shipping country/region** column. To delete a selected record, select **Delete** on the Action Pane.
    - If you're creating a new record, on the Action Pane, select **New**.
1. The details page for your new or selected record opens. Use the settings on the **General** tab to define the shipping address, receiving address, and the number of days needed to transport goods between them. For more information about each field, hover your mouse pointer over the field label to open a tooltip. Here are a few tips for filling out the fields:
    - A convenient way to fill out an address is to start by entering the **Shipping ZIP/postal code**. Often, then system can automatically fill out the rest of the address for you based on this.
    - When calculating the ship date, the system uses the most specific purchase transport days record it can find. For example, suppose you have just two purchase transport days records: one for Spain to USA of 30 days and another for Madrid to New York of 20 days. In this case, a purchase order shipping from Madrid to New York would use 20 days, while an order from Valencia to New York would use 30 days.
1. On the **Transport days per mode of delivery** FastTab, you can set specific transport days for any number delivery modes (such as road, rail, and air). Use the buttons on the FastTab toolbar to add and remove rows here as needed.
    - For each row, select a mode of delivery and then specify the number of transport days for that mode.
    - If you want one of these modes to be the default transport days (which apply for all modes not specified here), then mark the **Default** checkbox for that row.
    - If none of the rows on the **Transport days per mode of delivery** FastTab is marked as **Default**, then the **Transport in days** value specified on the **General** FastTab is the default travel time.
1. On the Action Pane, select **Save**.

## Vendor settings for calculating requested ship dates

To calculate requested ship dates, you must set up an address for each vendor. To help make the calculation even more accurate, you can also set up vendor ship calendars that define on which specific days each vendor can ship.

### Set up vendor addresses

To set up addresses for a vendor, go to **Procurement and sourcing \> Vendors \> All vendors**, open the vendor record that you want to work with, and use the settings on the **Addresses** FastTab to add and remove addresses as needed. If more than one address is specified on the **Addresses** FastTab, then the system uses the address where **Primary** is set to *Yes* as the shipping point when using the **Purchase transport days** setup to calculate the shipping time.

### Assign vendor ship calendars

For each vendor, you can specify a ship calendar that indicates the dates on which that vendor is able to ship. For example, some vendors might be able to ship during all opening hours, while others might only ship on Mondays. You can define as many specific ship calendars as you need and then apply them to each vendor as appropriate. If you have goods that need to be expedited, and the relevant vendor makes an exception on their vendor ship calendar, you can change or remove the vendor ship calendar for the relevant purchase order lines.

For details about how to set up a ship calendar and define the available ship dates and times for it, see [Calendars and master planning](supply-chain-calendars-master-planning.md).

To assign a ship calendar to a vendor, follow these steps:

1. Go to **Procurement and sourcing \> Vendors \> All vendors**.
1. Open the vendor record that you want to assign a ship calendar to.
1. Expand the **Invoice and delivery** FastTab.
1. In the **Ship calendar** field, select the [ship calendar](supply-chain-calendars-master-planning.md) that applies to the vendor.

## Date calculations and recalculations

This section describes how and when the system calculates and recalculates requested ship dates.

### Requested ship date

The requested ship date calculation takes into account lead time (lead time per vendor if set up on trade agreements), mode of delivery, and the vendor ship calendar.

The lead time is the time it takes for the vendor to produce the item. It doesn't include transport days (from vendor to company).

You can configure how the system should handle requested ship dates that are in the past. For more information, see [Choose whether to allow requested ship dates to be in the past](#parameters).

### Order date on planned purchase orders

When a master planning run indicates that a planned order is needed, the order date is calculated backwards from the requirement date and takes into account margins, lead time, and the **Purchase transport days** setup. The requested ship date is calculated following the same rules as for purchase orders. However, the requested ship date isn't saved as a field value for planned orders, nor is it shown on the **Planned purchase order** details page.

The requested ship date is also calculated for manually created planned purchase orders.

### Recalculations for updated orders

When you edit a purchase order where the requested and/or confirmed ship date has already been calculated, the system makes the following recalculations:

- When **Requested ship date** is changed, the **Requested receipt date** is recalculated.
- When **Requested receipt date** is changed, the **Requested ship date** is recalculated.
- When **Confirmed ship date** is changed, the **Confirmed receipt date** is recalculated.
- When **Confirmed receipt date** is changed, the **Confirmed ship date** is recalculated.
- When any of the following are changed, then the relevant ship and receive dates are recalculated:
    - Address on the header
    - Mode of delivery (on the header or on a line)
    - Warehouse on a line

If you change the **Requested ship date** or **Confirmed ship date** on the header of a purchase order, the system asks you whether the relevant ship and receive dates should also be updated for each line.
