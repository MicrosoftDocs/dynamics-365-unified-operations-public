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
1. On the **Addresses** FastTab, add and remove addresses as you require. If more than one address is specified on the **Addresses** FastTab, when the system uses the purchase transport days setup to calculate the shipping time, it uses the address where the **Primary** option is set to *Yes* as the shipping point.

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
