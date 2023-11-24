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

Dynamic positive days help increase your sales order fulfillment rate by using on-hand inventory and planned receipts for last-minute orders. When you use dynamic positive days, master planning will apply the following rules to determine whether to create a new planned order or use existing supply:

- When an item is needed outside of its lead time, master planning will suggest creating a new planned order.
- When an item is needed within the lead time, master planning will suggest using existing supply.

When a customer requests an item to be delivered outside of that item's lead time, then the system shouldn't peg the sales order against existing purchase orders that are confirmed before the requested ship date on the sales order. Instead, the sales order should be pegged against a new planned purchase order. This strategy allows sales orders that are created later, but are requested earlier than the first sales order, to use the existing purchase orders. It lets you fulfill all demand while better managing your supply and delivery dates (including when using capable to promise).

<!--KFM: Definitions of "positive days" and "dynamic positive days" are needed. Make it clear how they are different. Link to [Master plans overview](master-plans.md)-->

The system doesn't only use the lead time when deciding which supply to peg, but outside of the lead time, it also takes into account the positive days. The number of positive days that apply for a given item are set on its item coverage group, and this value can be overwritten at the master plan level. This allows certain master plans to have a higher number of positive days than others, allowing different plans to be used for capable to promise versus actual for the day-to-day business.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use dynamic positive days, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Dynamic positive days for Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up your system to use positive days

Follow these steps to set up your system to use positive days:

1. Go to **Master planning \> Setup \> Master planning parameters**.
1. Open the **General** tab.
1. Set **Use dynamic positive days** to *Yes*.
1. On the Action Pane, select **Save**.

This setting applies all legal entities (companies) and master plans in your Supply Chain Management environment.

## Assign the number of positive days to an item coverage group

## Assign the number of positive days to a master plan

## Example scenarios

This section provides few example scenarios to help you understand how dynamic positive days work.

### Example scenario 1: Demand inside of the lead time

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

## Example scenario 2: Demand outside of the lead time

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

## Example scenario 3: Sales order within the positive days but outside of the lead time

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
