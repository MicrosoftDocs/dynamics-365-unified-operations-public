---
title: Dynamic positive days for last-minute orders
description: Dynamic positive days help increase your sales order fulfillment rate by using on-hand inventory and planned receipts for last-minute orders.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/17/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Dynamic positive days for last-minute orders

[!include [banner](../includes/banner.md)]

Dynamic positive days help increase your sales order fulfillment rate by using on-hand inventory and planned receipts for last-minute orders. When you use dynamic positive days, master planning applies the following rules to determine whether to create a new planned order or use existing supply:

- When an item is needed outside of its lead time, master planning suggests creating a new planned order.
- When an item is needed within the lead time, master planning suggests using existing supply.

This strategy allows sales orders that are created later, but requested earlier, than another sales order to use existing purchase orders. It lets you fulfill all demand while better managing your supply and delivery dates (including when using capable to promise).

The system doesn't only use the lead time when deciding which supply to peg. Outside of the lead time, it also takes into account the positive days. The number of positive days that apply for a given item are set on its item coverage group, and this value can be overwritten at the master plan level. This strategy allows certain master plans to have a higher number of positive days than others, allowing different plans to be used for capable-to-promise than for day-to-day business.

## Prerequisites

To use dynamic positive days, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Dynamic positive days for Planning Optimisation* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up your system to use dynamic positive days

Follow these steps to set up your system to use dynamic positive days:

1. Go to **Master planning \> Setup \> Master planning parameters**.
1. Open the **General** tab.
1. Set **Use dynamic positive days** to *Yes*.
1. On the Action Pane, select **Save**.

This setting applies all legal entities (companies) and master plans in your Supply Chain Management environment.

## Assign the number of positive days to an item coverage group

Follow these steps to assign the number of positive days to an item coverage group:

1. Go to **Master planning \> Setup \> Coverage \> Coverage groups**.
1. Select an existing coverage group or create a new one.
1. On the **General** FastTab, set **Positive days** to the number of days that you want to use for this coverage group.

## Example scenarios

This section provides few example scenarios to help you understand how dynamic positive days work.

### Example scenario 1: Demand inside of the lead time

The following scenario shows how the system handles demand requested for inside of the lead time.

1. Assume your system is set up as follows:

    - You have an item that belongs to a coverage group set up with 3 positive days and 3 negative days.
    - The lead time of the item is 5 days.
    - Dynamic positive days are enabled.
    - Your master plans do not include any positive days overrides.
    - You have a purchase order for the item that is scheduled to be delivered in on day 2.

1. A new sales order is now created for the item. The requested ship date is day 3.
1. The system therefore pegs the new sales order to the existing purchase order because the requested ship date is within the lead time.

:::image type="content" source="media/dynamic-pos-days-scenario-1.png" alt-text="Timeline for example scenario 1":::

## Example scenario 2: Demand outside of the lead time

The following scenario shows how the system handles demand requested for outside of the lead time.

1. Assume your system is set up as follows:

    - You have an item that belongs to a coverage group set up with 3 positive days and 3 negative days.
    - The lead time of the item is 5 days.
    - Dynamic positive days are enabled.
    - Your master plans do not include any positive days overrides.
    - You have a purchase order (PO1) for the item that is scheduled to be delivered on day 2.
    - You have a second purchase order (PO2) for the item that is scheduled to be delivered on day 6.

1. The following sales orders are now created for the item:

    - Sales order 1 (SO1) has a requested ship date of day 10.
    - Sales order 2 (SO2) has a requested ship date of day 3.

1. The system therefore takes the following actions:

    - Peg SO2 against the existing PO1.
    - Create a new planned purchase order (PPO) and peg SO1 against it.

    Because SO1 is outside of the lead time, the system create a new planned order to supply it (there is no supply within the positive days).

:::image type="content" source="media/dynamic-pos-days-scenario-2.png" alt-text="Timeline for example scenario 2":::

## Example scenario 3: Sales order within the positive days but outside of the lead time

The following scenario shows how the system handles demand requested within the positive days but outside of the lead time.

1. Assume your system is set up as follows:

    - You have an item that belongs to a coverage group set up with 3 positive days and 3 negative days.
    - The lead time of the item is 5 days.
    - Dynamic positive days are enabled.
    - Your master plans do not include any positive days overrides.
    - You have a purchase order (PO1) for the item that is scheduled to be delivered on day 2.
    - You have a second purchase order (PO2) for the item that is scheduled to be delivered on day 8. (Unlike previous example, this second purchase order is now scheduled for delivery within the positive days range.)

1. The following sales orders are now created for the item:

    - Sales order 1 (SO1) has a requested ship date of day 10.
    - Sales order 2 (SO2) has a requested ship date of day 3.

1. The system therefore takes the following actions:

    - Peg SO1 against the existing PO1.
    - Peg SO2 against the existing PO2.

:::image type="content" source="media/dynamic-pos-days-scenario-3.png" alt-text="Timeline for example scenario 3":::
