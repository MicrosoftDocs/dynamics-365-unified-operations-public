---
title: Supplier requested and confirmed dates (preview)
description:
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/16/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Supplier requested and confirmed dates (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

<!--KFM: Confirm preview date and add to appropriate What's new -->

If you have vendors without specific delivery terms, such as delivery duty paid, delivery at place, or delivery at place unloaded, you must tell them when they should ship. This feature adds a new ship date field to purchase orders, calculated according to the configured transport dates.

Purchase orders in Dynamics 365 Supply Chain Management currently include a *delivery date*, which specifies when the order should be received at your company's location. This feature adds a *ship date*, specifying the date the vendor should ship from their location.

The system calculates the ship date according to the new transportation days setup, which lets you define the number of days needed to transport items between a vendor's location and your locations. When master planning suggests a date for placing a planned order, it will also consider the transportation days setup to help make sure the goods will arrive at your location on time.

You can also choose to set up a vendor ship calendar to define the days a vendor can ship. When some goods need to be expedited, and a vendor makes an exception on their vendor ship calendar, you can accommodate this by changing or removing the vendor ship calendar for the relevant purchase order lines.

![A diagram of a company Description automatically generated](media/image1.png)

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Setup

To enable the supplier requested and confirmed dates, the following feature must be enabled in feature management, available from 10.0.38:

"Supplier requested and confirmed dates"

With this feature the following functionality and setup is included in the application.

## Requested ship date and confirmed ship date on purchase orders

New fields are introduced to indicate the ship date and confirmed ship date when vendors should ship the orders so they arrive on time to the corresponding requested delivery date and confirmed receipt date.

Note with the 10.0.38 release the purchase order fields **requested delivery date** and **confirmed delivery date** are renamed to **requested receipt date** and **confirmed receipt date**, aligning with how the fields are called for Sales orders.

## Purchase transport days

A new form called **Purchase transport days** is introduced so that the needed transport days. Note that this form is an address to address form, so that:

- If you need to specify the transport from a certain vendor to one of your warehouses, you must include the address of your warehouse.
- There is not a specific address for a vendor, a vendor can have many addresses
- The most specific address will be taken. For example, if there are two transport days one for Spain to US of 20 days and another one between cities in those countries (Valencia to New York) of 30 days. If the purchase order has the city to city (Valencia to New York), then that transport days of 20 days will be taken.
- This is also useful is any of the delivery addresses of the lines is changed, so it can be the most specific possible.

## Vendor shipping calendar

For a given vendor, a new field is introduced indicating the Vendor ship calendar that can be used to indicate in which dates the vendor is able to ship. For example, it may be all days that the vendor is open or that the vendor may only be able to send shipments a certain day of the week (like Mondays, so a calendar open only Mondays could be entered).

The vendor ship calendar is located under the tab **Purchase and Delivery** for the vendor details page.

Remember that the addresses for the vendor are kept under the tab **Addresses** on the vendor details page.

## Calculation of the ship date, receipt date and updates

### Requested ship date

Requested ship date is calculated taking into account lead time (lead time per vendor if setup on trade agreements), mode of delivery and vendor shipping calendar).

It is expected that the lead time is the time it takes for the vendor to produce the item. It does NOT include the transport days (from vendor to company).

Ship date must be calculated backwards from the receipt date, transport days and finding the previous open date on the vendor ship calendar.

The vendor ship date must be &gt;= today. If prior to today, then ship date and receipt dates must be recalculated according to the first feasible ship date.

Note confirmed dates can be in the past.

### Requested receipt date (existing field)

This field currently is calculated according to the lead time of the item.

It must be modified so that it also takes into account the transport days (lead time + transport days)

### Order date on planned purchase order

Order date on planned purchase order must also be modified so that when calculating backwards from requirement date it makes sure that a part of the lead time, the new transport days are taking into account, and that the shipping date (not saved as a field on the planned purchaser order but should be taken into account in the calculation) must be an open day in the vendor calendar.

NOTE classic master planning is OUT OF SCOPE

### Updates between the dates

- When Requested ship date is changed, Receipt date must be recalculated.
- When Receipt date is changed, Ship date must be recalculated.
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

Ship date will also be calculated

### On purchase order confirmation

Ship date will also be added

Note the calculation will not be applicable to:

- receipt journal and invoice journal.
- RFQ reply
- receipt journal, invoice journal, Vendor collaboration
- History

## Ship date in the past

There is a parameter indicating if the ship dates should or should not be allowed in the past. It can be found under **Procurement and sourcing parameters** form, Delivery tab.

This parameter allows you to specify the default value for validation of the requested ship date if it is in the past. The options are:

- **None**: if you want to allow requested ship dates to be in the past.
- **Allow with warning**: if you would like to allow requested ship dates in the past but show a warning message.
- **Disallow with warning**: if the requested ship dates should always be calculated again from today's date and a warning message should be shown.

## Ship date in master planning

When needing to calculate the order date, it will take into account the transport dates, so that the order date is calculated backwards from the requirement date taking into account margins, transport days and lead time.

The ship date is calculated following the same rules as with purchase orders. However, this date is not shown in the planned purchase order form.

Note this only applies for the current master planning engine and not the deprecated planning.
