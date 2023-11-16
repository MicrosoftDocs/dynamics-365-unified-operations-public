---
title: Dynamic positive days for last-minute orders (preview)
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

# Dynamic positive days for last-minute orders (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

Increase your order fulfillment rate by using on-hand inventory and planned receipts for last-minute orders. Master planning will suggest creating a new planned order when an item is needed outside of its lead time while using existing supply if it is needed within the lead time. You can control this using the **Dynamic positive days** parameter.

To enable this feature you must enable the following feature on feature management, available from 10.0.38:

- Dynamic positive days for Planning Optimization

And then setup the system to use Dynamic positive must be done by enabling the parameter **Use dynamic positive days** on the **Master planning parameters** page, under the **General** tab. It applies to the whole system, all your companies and master plans.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Why use dynamic positive days

If a sales order is wanted outside the item's lead time, then we do not want the sales order to be pegged against existing purchase orders that are confirmed before the requested ship date on the sales order. Instead, the sales order should be pegged against a new planned purchase order.

The reason is that sales orders that are created subsequently and that are requested earlier than the first sales order will be able to use the existing purchase orders. With this, it will be possible to fulfill all the sales orders demand, and in general, provide better supply and dates (including when using capable to promise).

## Master planning calculation

Master planning will suggest creating a new planned order when an item is needed outside of its lead time while using existing supply if it is needed within the lead time.

It is not just the lead time that is used for evaluation, but outside of the lead time, it will take into account the positive days.

Note the number of positive days for a given item are set on the Item coverage group associated, and they can be overwritten at the master plan level. This allows certain master plans to have a higher number of positive days than others, allowing different plans to be used for capable to promise versus actual for the day-to-day business.

## Example 1: demand inside of the lead time

*Given:*

- Item with coverage group setup 3 days in positive days and 3 days in negative days
- Lead time of item = 5 days
- Dynamic positive days is used
- No overwrite of positive days on Masterplans
- A purchase order for day 2

*When:*

- Sales order created for item – requested date = day 3

*Then:*

- Sales order pegged against purchase order = customer can get as requested
- Summary: as the sales order is inside of the lead time, it gets pegged with any existing supply

![A line of days and numbers Description automatically generated](media/image1.png)

## Example 2: demand outside of the lead time

*Given:*

- Item with coverage group setup 3 days in positive days and 3 days in negative days
- Lead time of 5 item = 5 days
- Dynamic positive days is used
- No overwrite of positive days on Masterplans
- A purchase order for day 2
- A purchase order for day 6

*When:*

- SO2 created for item – requested date = day 3
- SO1 created for item – requested date = day 10

*Then:*

- SO2 pegged towards PO1
- SO1 pegged against planned purchase order
- Summary: as the sales order is outside of the lead time, a new planned order is created to supply it (note there is no supply within the positive days)

![A screenshot of a graph Description automatically generated](media/image2.png)

## Example 3: sales order within the positive days but outside of the lead time

*Given:*

- Item with coverage group setup 3 days in positive days and 3 days in negative days
- Lead time of 5 item = 5 days
- Dynamic positive days is used
- No overwrite of positive days on Masterplans
- A purchase order for day 2
- A purchase order for day 8 (note this is the difference with the previous example 2, where the purchase order is now inside of the positive days)

*When:*

- SO2 created for item – requested date = day 3
- SO1 created for item – requested date = day 10

*Then:*

- SO1 pegged against PO1
- SO2 pegged against PO2

![A graph with numbers and arrows Description automatically generated](media/image3.png)
