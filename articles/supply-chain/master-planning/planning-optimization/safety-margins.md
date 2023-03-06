---
# required metadata

title: Safety margins
description: This article describes how safety margins work during master planning.
author: t-benebo
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2020-9-14
ms.dyn365.ops.version: AX 10.0.13

---
# Safety margins

[!include [banner](../../includes/banner.md)]

This article describes how safety margins work during master planning.

## Safety margins overview

The purpose of safety margins is to enable a setup that provides some buffer time beyond the normal lead time. For example, when material must be unpacked or inspected after it arrives from the vendor, you can't just add the extra time to the purchase lead time, because this approach will give the additional buffer time to the supplier. In this example, the receipt margin can be used to ensure that the supplier delivers earlier. This approach provides buffer time so that the goods can be handled internally.

There are three types of safety margins:

- **Reorder margin** – The buffer time for placing the supply order
- **Receipt margin** – The buffer time for handling incoming supply
- **Issue margin** – The buffer time for handling shipments

The following illustration shows how these safety margins apply over time.

![Safety margins.](media/safety-margins-1.png)

All margins are defined in days. The default value, *0* (zero), indicates that no margin is applied. If you set up multiple margins, they all add to the total time from the supply *order date* to the demand *requirement date*. For example, a setup has no lead time, and all three margin types are set to one day. In this case, there will be three days between the supply order date and the demand requirement date, so if the order date is July 1, the requirement date would be July 4.

### Receipt margin

The receipt margin is probably the most used of the three safety margins. It's applied to the *delivery date* and backward from the *requirement date*. In other words, the products should be received the specified number of receipt margin days before they are required.

The following illustration highlights the receipt margin.

![Receipt margin.](media/safety-margins-2.png)

The receipt margin is typically used as a buffer to ensure time for warehouse registration or other time-consuming processes that aren't captured as part of the general lead time in the system. For purchases, one benefit is that the *delivery date* of the purchase order is moved forward accordingly. If you  increase the lead time instead of using a safety margin, the vendor will still be asked to deliver at the last minute.

Notice that the receipt margin doesn't change the *requirement date* of the supply. Therefore, the receipt margin isn't directly visible when requirement dates for demand and supply are compared (for example, on the **Net requirements** page). For example, if the receipt margin is set to four days, and a purchase order line is planned for receipt on the fifteenth of the month, master planning calculates the adjusted receipt date as the nineteenth of the month.

Note that a receipt margin isn't applied when on-hand inventory is used as the supply. All on-hand inventory is assumed to be available immediately, regardless of when it was actually received.

### Reorder margin

The following illustration highlights the reorder margin.

![Reorder margin.](media/safety-margins-3.png)

The reorder margin is added before the item lead time for all planned orders during master planning. Therefore, it ensures additional time for a supply order to be placed. This margin is typically used as a buffer to ensure time for approval processes or other internal processes that are required during the creation of supply orders. The reorder margin is put between the supply *order date* and *start date*.

### Issue margin

The following illustration highlights the issue margin.

![Issue margin.](media/safety-margins-4.png)

The issue margin is deducted from the demand requirement date during master planning. It helps ensure that you have time to react to and ship incoming demand orders. This margin is typically used as a buffer to ensure time for shipment and related outbound warehouse processes.

Notice that when an issue margin is applied, related supply and demand requirement dates don't match. Instead, they differ by the issue margin, because the issue margin is added between the supply *requirement date* and the demand *requirement date*.

## Set up safety margins

### Turn safety margins on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Margins for Planning Optimization* feature in the [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Define safety margins

Safety margins have a flexible setup. They can be set on both the *coverage group* and the *master plan*. It's important that you understand that the margins are added on top of each other. For example, a receipt margin of two days on the coverage group and three days on the master plan will produce an effective receipt margin of five days.

The ability to set the margin on the master plan can be useful when you want to simulate longer lead times or uncertainty for a specific plan, but without affecting the daily planning.

#### Coverage group safety margins

To apply a safety margin to a coverage group, follow these steps.

1. Go to **Master planning \> Setup \> Coverage groups**.
1. In the list pane, select the desired coverage group.
1. On the **Other** FastTab, in the **Safety margins in days** section, use the following fields to set the required safety margins (in days):

    - Receipt margin added to requirement date
    - Issue margin deducted from requirement date
    - Reorder margin added to item lead time

#### Master plan safety margins

To apply a safety margin to a master plan, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. In the list pane, select the desired master plan.
1. On the **Safety margins in days** FastTab, use the following fields to set the required safety margins (in days):

    - Receipt margin added to requirement date
    - Issue margin deducted from requirement date
    - Reorder margin added to item lead time

### Define whether calculations are based on calendar days or work days

You can set all safety margins so that they are calculated based on either calendar days or work days.

1. Go to **Master planning \> Setup \> Master planning parameters**.
1. On the **General** tab, in the **Safety margins in days** section, set the **Working days** option to *Yes* to calculate margins based on working days. Set the option to *No* to calculate margins based on calendar days.

For example, a calendar is open from Monday through Friday and closed from Saturday through Sunday. If there is a receipt margin of one day, a requirement date on a Monday produces a delivery date on the previous Friday, because Saturday and Sunday aren't working days.

The calendar that is used to determine the working days depends on the setup and the supply type. It can be controlled by the calendars of the coverage group, the warehouse, and the vendor.

> [!NOTE]
> If *warehouse* isn't part of the coverage dimension (in other words, planning is based only on *site*), the warehouse calendar isn't used.

The system can handle a setup where one or more calendars are defined. The following subsections describe the possible combinations that can be used to control the result.

#### Calendar that is used for the duration

The defined calendars control the actual total lead time in calendar days, from the supply order date to the demand requirement date. The following calendar prioritization is used:

- **Purchase lead time** – Only the coverage group calendar is considered.
- **Receipt margin** – The coverage group calendar is used, if it's defined. Otherwise, the warehouse calendar is used.
- **Issue margin** – The coverage group calendar is used, if it's defined. Otherwise, the warehouse calendar is used.
- **Order margin** – Only the coverage group calendar is considered.

#### Calendar that is used for the final date

The following rules are applied to determine whether the planning engine can use a given date for a given date type:

- **Purchase receipt date** – The vendor calendar is used, if it's defined. Otherwise, the coverage group calendar is used, if it's defined. If neither of those calendars is defined, the warehouse calendar is used.
- **Transfer receipt date** – The coverage group calendar is used, if it's defined. Otherwise, the warehouse calendar is used.
- **Production receipt date** – The coverage group calendar is used, if it's defined. Otherwise, the warehouse calendar is used.
- **Demand issue open day** – The warehouse calendar is used, if it's defined. Otherwise, the coverage group calendar is used.
- **Order open day** – A combination (intersection) of the coverage group calendar and the vendor calendar is used. Both calendars must be open to use the date. If only one of the calendars is defined, that calendar is used alone.

#### Calendar setup overview matrix

The following illustration presents a matrix that summarizes which calendars apply when safety margins are calculated. (Select the image to open a high-resolution version of it.) The following abbreviations and colors are used to indicate where each type of calendar is specified:

- **Coverage group (CG):** Green
- **Warehouse (WH):** Yellow
- **Vendor (V):** Blue

[![Calendar setup overview matrix.](media/safety-margins-calendar-matrix.png)](media/safety-margins-calendar-matrix-high.png)

## Calculating delays

All three types of safety margins are included when the system determines whether an order is delayed.

For example, an item has lead time of one day and a receipt margin of three days. A sales order for this item is set as required today. In this case, the delay is calculated as *lead time* + *receipt margin* = four days. Therefore, if today is August 14, the four days of delay produces a delivery on August 18. The following illustration shows this example.

![Delay calculation example.](media/safety-margins-delays.png)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]