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

This topic describes how safety margins can be used with Planning Optimization.

## Safety margins overview

The purpose of safety margins is to enable a setup with some buffer time beyond the normal lead time. An example is that material needs to be unpacked or inspected after arrival from the vendor. In this scenario we can&#39;t just add the extra time to the purchase lead time, as this would just give the supplier the additional buffer time. In this example receipt margin can be used to ensure that the supplier delivers earlier, so that we have the buffer time for internal handling of the goods.

There are three types of safety margins.

1. **Reorder margin** – buffer time for placing the supply order
2. **Receipt margin** – buffer time for handling incoming supply
3. **Issue margin** – buffer time for handing shipment

![](RackMultipart20200818-4-1hxafz0_html_8f8f263be12168f0.png)

All margins are defined in days. Default value is 0 (zero), meaning that no margin is applied. If you setup multiple margins, they will all add to the total time from supply **Order date** to demand **Requirement date**.

Example: A setup with no lead time and 1 day for all 3 margin types will result in 3 days between supply **Order date** and demand **Requirement date**.

### Receipt margin

Receipt margin is probably the most used of the three safety margins. It is applied to the delivery date, backward from the **Requirement date**. Meaning that the products should be received &#39;Receipt margin days&#39; before they are required.

![](RackMultipart20200818-4-1hxafz0_html_43c372830ccdac3.png) This is typically used as a buffer to ensure time for warehouse registration, or other time-consuming processes that are not captured as part of the general lead time in the system. For purchase it gives the benefit that the **Delivery date** of the purchase order is moved forward accordingly. If the lead time was increased, instead of using a safety margin, then the vendor would still be asked to deliver last minute.

Notice that the **Requirement date** of the supply is not changed by the receipt margin. This means that the receipt margin is not visible directly when comparing requirement dates for demand and supply, e.g. on the **Net requirements** form.

For example, if the receipt margin is set to 4 days and a purchase order line is planned for receipt on the 15th of the month, then master planning calculates the adjusted receipt date as the 19th of the month.

Note that Receipt margin is not applied when using on-hand as the supply. All on-hand is assumed to be available immediately, regardless of when it was actually received.

### Reorder margin

> [!NOTE]
> _**Coming soon** – currently not supported with Planning Optimization. Until supported, values in **Reorder margin added to item lead time** will be treated as zero (0)._

![](RackMultipart20200818-4-1hxafz0_html_db8c1ca43e75c6e8.png)

The Reorder margin is added prior to the item lead time for all planned orders during master planning, ensuring additional time for placing a supply order.

This is typically used as a buffer to ensure time for approval processes or other internal processes needed during creation of supply orders. Reorder margin is placed between the Supply **Order date** and **Start date**.

### Issue margin

> [!NOTE]
> _**Coming soon** – currently not supported with Planning Optimization. Until supported, values in **Issue margin deducted from requirement date** will be treated as zero (0)._

![](RackMultipart20200818-4-1hxafz0_html_14c6f28fbdb66622.png)

The Issue margin is deducted from the demand requirement date during master planning. Ensuring time to react on and ship incoming demand orders. This is typically used as a buffer to ensure time for shipment and related outbound warehouse processes.

Notice that when an Issue margin is applied related supply and demand requirement dates will not match, they will differ by the Issue margin – as the issue margin is added between the supply requirement date and the demand requirement date.

## Setup

### Enable Safety margins in Feature management

Before you can use this feature with Planning Optimization, it must be turned on in your system. Admins can use the [Feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) workspace to check the status of the feature and turn it on if it&#39;s required. There, the feature is listed in the following way:

- **Module:**  _Master planning_
- **Feature name:**  _Margins for Planning Optimization_

### Define safety margins

Safety margins comes with a flexible setup that can be set both on the **Coverage group** and on the **Master plan**. It is important to notice that the margins are added on top of each other. Example: A **Receipt margin** of 2 days on the **Coverage group** and 3 days on the **Master plan** will result in an effective **Receipt margin** of 5 days.

Setting the margin on the master plan can be useful for simulating longer lead times or uncertainty with a specific plan, without affecting the daily planning.

#### Coverage group

Safety margins can be applied by going to  **Master planning** > **Setup** > **Coverage groups**, select the desired **Coverage group**. Safety margins are defined in number of days from the fast tab **Other,** under **Safety margins in days** , with the following fields:

- **Receipt margin added to requirement date**
- **Issue margin deducted from requirement date**
- **Reorder margin added to item lead time**

#### Master plan

Safety margins can be applied by going to  **Master planning** > **Setup** > **Plans** > **Master plans**, select the desired **Master plan**. Safety margins are defined in number of days from the fast tab **Safety margins in days** , with the following fields:

- **Receipt margin added to requirement date**
- **Issue margin deducted from requirement date**
- **Reorder margin added to item lead time**

### Calendars

Safety margins can be set to **Working days** on the **Master planning parameters**.

**Master planning** > **Setup** > **Master planning parameters**

With **Safety margins in days** set to use **Working days** the margin will be added as working days in the calendar.

Example: A calendar is open Monday to Friday and closed Saturday to Sunday. With a receipt margin of one day a **Requirement date** on a Monday would result in a **Delivery date** of the supply on the previous Friday, as Saturday to Sunday are closed and hence non-working days.

The calendar used to determine the working days depends on the setup and supply type. It can be controlled by the calendar of the **Coverage group** , the calendar of the **Warehouse** , and the calendar of the **Vendor**.

Note: If warehouse is not part of the coverage dimension, i.e. planning on site only, then the warehouse calendar not used.

The system can handle a setup with one or more calendars defined, the following covers the possible combinations that can be used to control the result.

#### Calendar used for duration

The actual total lead time in calendar days, from supply order date to demand requirement date, is controlled by the defined calendars.

The following calendar prioritization is used:

- Purchase lead time: Only Coverage Group calendar is considered
- Receipt margin: Coverage Group calendar, if defined, else Warehouse calendar
- Issue margin: Coverage Group calendar, if defined, else Warehouse calendar
- Order margin: Only Coverage Group calendar is considered

#### Calendar used for final date

To determine if a given date is available for the planning engine to use for the given date type.

- Purchase receipt date: Vendor calendar if defined, else Coverage Group calendar if defined or finally Warehouse calendar is used.
- Transfer receipt date: Coverage Group calendar, if defined, else Warehouse calendar
- Production receipt date: Coverage Group calendar, if defined, else Warehouse calendar
- Demand Issue open day: Warehouse calendar, if defined, else Coverage Group calendar
- Order open day: Use a combination (Intersection) of Coverage group and Vendor calendar, where both needs to be open to use the date. If only one of the calendars are defined, then this calendar is used alone.

#### Calendar setup overview matrix

![](RackMultipart20200818-4-1hxafz0_html_7fc545c957af833a.jpg)

## Calculating delays

All 3 types of safety margins are included when determining if an order is delayed.

Example: Given an item with a lead time of 1 day and a receipt margin of 3 days. When we have a demand for a sales order for this item, that is required today. Then there will be a delay of the lead time + receipt margin = 4 days. In case today is August 14th, then the 4 days of delay would result in a delivery on the 18th.

![](RackMultipart20200818-4-1hxafz0_html_81ee749a52b0d5a9.png)

## Additional resources

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
