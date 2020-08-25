---
# required metadata

title: Safety margins
description: This topic describes how safety margins works with Planning Optimization.
author: ChristianRytt
manager: tfehr
ms.date: 08/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-8-18
ms.dyn365.ops.version: AX 10.0.13

---
# Safety margins 

[!include [banner](../../includes/banner.md)]

This topic describes how safety margins can be used with the Planning Optimization Add-in for Microsoft Dynamics 365 Supply Chain Management.

## Safety margins overview

The purpose of safety margins is to enable a setup with some buffer time beyond the normal lead time. An example is that material needs to be unpacked or inspected after arrival from the vendor. In this scenario, we can't just add the extra time to the purchase lead time because this would just give the supplier the additional buffer time. In this example, the receipt margin can be used to ensure that the supplier delivers earlier, and thereby provide buffer time to handle the goods internally.

There are three types of safety margins:

- **Reorder margin** – buffer time for placing the supply order
- **Receipt margin** – buffer time for handling incoming supply
- **Issue margin** – buffer time for handing shipment

The following diagram shows how these safety margins apply over time.

![Safety margins](media/safety-margins-1.png)

All margins are defined in days. Default value is 0 (zero), meaning that no margin is applied. If you set up multiple margins, they will all add to the total time from the supply *order date* to the demand *requirement date*.

For example, a setup with no lead time and all thee margin types set to one day will result in three days between the supply order date and the demand requirement date.

### Receipt margin

Receipt margin is probably the most used of the three safety margins. It is applied to the delivery date and backward from the *requirement date*. Meaning that the products should be received "Receipt margin days" before they are required.

The following diagram highlights the receipt margin.

![Safety margins](media/safety-margins-2.png)

This is typically used as a buffer to ensure time for warehouse registration, or other time-consuming processes that are not captured as part of the general lead time in the system. For purchases, it gives the benefit that the *delivery date* of the purchase order is moved forward accordingly. If the lead time was increased, instead of using a safety margin, then the vendor would still be asked to deliver at the last minute.

Notice that the *requirement date* of the supply is not changed by the receipt margin. This means that the receipt margin is not visible directly when comparing requirement dates for demand and supply (for example, on the **Net requirements** page).

For example, if the receipt margin is set to four days and a purchase order line is planned for receipt on the 15th of the month, then master planning calculates the adjusted receipt date as the 19th of the month.

Note that receipt margin is not applied when using on-hand as the supply. All on-hand is assumed to be available immediately, regardless of when it was actually received.

### Reorder margin

> [!NOTE]
> _**Coming soon** – This feature isn't yet supported for Planning Optimization. Until supported, all values entered for **Reorder margin added to item lead time** will be treated as zero (0)._

The following diagram highlights the reorder margin.

![Safety margins](media/safety-margins-3.png)

The reorder margin is added prior to the item lead time for all planned orders during master planning, ensuring additional time for placing a supply order.

This is typically used as a buffer to ensure time for approval processes or other internal processes needed during creation of supply orders. Reorder margin is placed between the Supply *order date* and *start date*.

### Issue margin

> [!NOTE]
> _**Coming soon** – This feature isn't yet supported for Planning Optimization. Until supported, all values entered for **Issue margin deducted from requirement date** will be treated as zero (0)._

The following diagram highlights the issue margin.

![Safety margins](media/safety-margins-4.png)

The issue margin is deducted from the demand requirement date during master planning. It helps ensure time to react to and ship incoming demand orders. This is typically used as a buffer to ensure time for shipment and related outbound warehouse processes.

Notice that when an issue margin is applied, related supply and demand requirement dates will not match. Instead, they will differ by the Issue margin because the issue margin is added between the supply requirement date and the demand requirement date.

## Set up safety margins

### Enable safety margins in feature management

Before you can use this feature with Planning Optimization, it must be turned on in your system. Admins can use the [Feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

- **Module:**  _Master planning_
- **Feature name:**  _Margins for Planning Optimization_

### Define safety margins

Safety margins comes with a flexible setup that can be set on both the *coverage group* and *master plan*. It is important to notice that the margins are added on top of each other. For example, a *receipt margin* of 2 days on the coverage group and 3 days on the master plan will result in an effective *receipt margin* of 5 days.

Setting the margin on the master plan can be useful for simulating longer lead times or uncertainty with a specific plan, without affecting the daily planning.

#### Coverage group safety margins

To apply a safety margin to a coverage group:

1. Go to **Master planning \> Setup \> Coverage groups**.
1. Select the desired coverage group from the list pane.
1. Expand the **Other** FastTab.
1. Set the safety margins (in days) as required using the following fields from the **Safety margins in days** section:
    - **Receipt margin added to requirement date**
    - **Issue margin deducted from requirement date**
    - **Reorder margin added to item lead time**

#### Master plan safety margins

To apply a safety margin to a master plan:

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select the desired master plan from the list pane.
1. Expand the **Safety margins in days** FastTab.
1. Set the safety margins (in days) as required using the following fields:
    - **Receipt margin added to requirement date**
    - **Issue margin deducted from requirement date**
    - **Reorder margin added to item lead time**

### Calendars

You can set all safety margins to be calculated based on calendar days or on work days. To set this option:

1. Go to **Master planning \> Setup \> Master planning parameters**
1. Open the **General** tab.
1. In the **Safety margins in days** section, set **Working days** to *Yes* to calculate margins based on working days. Set it to *No* to calculate based on calendar days.

For example, a calendar is open Monday to Friday and closed Saturday to Sunday. With a receipt margin of one day, a requirement date on a Monday would result in a delivery date on the previous Friday because Saturday to Sunday are non-working days.

The calendar used to determine the working days depends on the setup and supply type. It can be controlled by the calendars of the *coverage group*, the *warehouse*, and the *vendor*.

> [!NOTE]
> If warehouse is not part of the coverage dimension (in other words, planning is only based on site) then the warehouse calendar isn't used.

The system can handle a setup with one or more calendars defined. The following subsections describe the possible combinations that can be used to control the result.

#### Calendar used for duration

The actual total lead time in calendar days, from supply order date to demand requirement date, is controlled by the defined calendars.

The following calendar prioritization is used:

- **Purchase lead time**: Only the coverage group calendar is considered.
- **Receipt margin**: The coverage group calendar is used, if defined. Otherwise the warehouse calendar is used.
- **Issue margin**: The coverage group calendar is used, if defined. Otherwise the warehouse calendar is used.
- **Order margin**: Only the coverage group calendar is considered.

#### Calendar used for final date

To determine whether a given date is available for the planning engine to use for a given date type, the following rules are applied:

- **Purchase receipt date**: The vendor calendar is used, if defined. Otherwise, the coverage group calendar is used, if defined. If neither is defined, the warehouse calendar is used.
- **Transfer receipt date**: The coverage group calendar is used, if defined. Otherwise the warehouse calendar is used.
- **Production receipt date**: The coverage group calendar is used, if defined. Otherwise the warehouse calendar is used.
- **Demand issue open day**: The warehouse calendar is sued, if defined. Otherwise the coverage group calendar is used.
- **Order open day**: Use a combination (intersection) of coverage group and vendor calendars, where both must be open to use the date. If only one of the calendars is defined, then that calendar is used alone.

#### Calendar setup overview matrix

The following chart summarizes which calenders apply when calculating safety margins. The following abbreviations and colors are used to indicate where each type of calendar is specified:

- CG (green): Coverage group
- WH (yellow): Warehouse
- V (blue): Vendor

![Safety margins](media/safety-margins-calendar-matrix.png)

## Calculating delays

All three types of safety margins are included when determining if an order is delayed.

For example, you have an item with a lead time of 1 day and a receipt margin of 3 days. We have a sales order for this item, which is set as required today. The delay will be: *lead time + receipt margin = 4 days*. So, if today is August 14th, then the 4 days of delay would result in a delivery on the 18th. The following diagram illustrates this example:

![Safety margins](media/safety-margins-delays.png)

## Additional resources

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
