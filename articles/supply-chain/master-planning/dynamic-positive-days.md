---
title: Dynamic positive days for last-minute orders
description: Learn about dynamic positive days and explains how to set up and use them, including an outline on setting up your system to use dynamic positive days.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 03/21/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Dynamic positive days for last-minute orders

[!include [banner](../includes/banner.md)]

Dynamic positive days help increase your sales order fulfillment rate by using on-hand inventory and planned receipts for last-minute orders. When you use dynamic positive days, master planning applies the following rules to determine whether to create a new planned order or use existing supply:

- If an item is needed outside its lead time, master planning suggests that a new planned order should be created.
- If an item is needed within its lead time, master planning suggests that existing supply should be used.

This strategy enables sales orders that are created later than, but requested earlier than, another sales order to use existing purchase orders. It lets you fulfill all demand and, at the same time, better manage your supply and delivery dates (including when you use capable-to-promise).

When the system determines which supply to peg, it doesn't just consider the lead time. It also considers the positive days. The number of positive days that apply to a given item are set on that item's item coverage group and can be overwritten at the master plan level. This strategy enables some master plans to have a higher number of positive days than others. Therefore, the plans that are used for capable-to-promise can differ from the plans that are used for day-to-day business.

## Prerequisites

Before you can use dynamic positive days, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that's named *Dynamic positive days for Planning Optimization* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up your system to use dynamic positive days

Follow these steps to set up your system to use dynamic positive days.

1. Go to **Master planning** \> **Setup** \> **Master planning parameters**.
1. On the **General** tab, set the **Use dynamic positive days** option to *Yes*.
1. On the Action Pane, select **Save**.

> [!NOTE]
> The **Use dynamic positive days** setting applies to all legal entities (companies) and master plans in your Supply Chain Management environment.

## Assign the number of positive days to an item coverage group

Follow these steps to assign the number of positive days to an item coverage group.

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. Select an existing coverage group, or create a new one.
1. On the **General** FastTab, set the **Positive days** field to the number of positive days that you want to use for the coverage group.

## Example scenarios

This section provides some example scenarios to help you understand how dynamic positive days work.

### Example scenario 1: Demand within the lead time

The following scenario shows how the system handles demand that's requested for a date that's within the lead time.

1. Your system is set up in the following way:

    - You have an item that belongs to a coverage group that's set up with three positive days and three negative days.
    - The lead time of the item is five days.
    - Dynamic positive days are enabled.
    - Your master plans don't include any positive day overrides.
    - You have a purchase order for the item. It's scheduled to be delivered on day 2.

1. A new sales order is created for the item. The requested ship date is day 3.
1. Because the requested ship date is within the lead time, the system pegs the new sales order to the existing purchase order.

:::image type="content" source="media/dynamic-pos-days-scenario-1.png" alt-text="Timeline for example scenario 1.":::

## Example scenario 2: Demand outside the lead time

The following scenario shows how the system handles demand that's requested for a date that's outside the lead time.

1. Your system is set up in the following way:

    - You have an item that belongs to a coverage group that's set up with three positive days and three negative days.
    - The lead time of the item is five days.
    - Dynamic positive days are enabled.
    - Your master plans don't include any positive day overrides.
    - You have a purchase order (PO1) for the item. It's scheduled to be delivered on day 2.
    - You have another purchase order (PO2) for the item. It's scheduled to be delivered on day 6.

1. The following sales orders are created for the item:

    - Sales order 1 (SO1) has a requested ship date of day 10.
    - Sales order 2 (SO2) has a requested ship date of day 3.

1. The system takes the following actions:

    - Peg SO2 against existing PO1.
    - Create a new planned purchase order, and peg SO1 against it.

    Because SO1 is outside the lead time, the system creates a new planned order to supply it. (There's no supply within the positive days.)

:::image type="content" source="media/dynamic-pos-days-scenario-2.png" alt-text="Timeline for example scenario 2.":::

## Example scenario 3: Sales order within the positive days but outside the lead time

The following scenario shows how the system handles demand that's requested for a date that's within the positive days but outside the lead time.

1. Your system is set up in the following way:

    - You have an item that belongs to a coverage group that's set up with three positive days and three negative days.
    - The lead time of the item is five days.
    - Dynamic positive days are enabled.
    - Your master plans don't include any positive day overrides.
    - You have a purchase order (PO1) for the item. It's scheduled to be delivered on day 2.
    - You have another purchase order (PO2) for the item. It's scheduled to be delivered on day 8. (Therefore, this example differs from the previous example in that PO2 is scheduled for delivery within the range of positive days.)

1. The following sales orders are created for the item:

    - Sales order 1 (SO1) has a requested ship date of day 10.
    - Sales order 2 (SO2) has a requested ship date of day 3.

1. The system takes the following actions:

    - Peg SO1 against existing PO1.
    - Peg SO2 against existing PO2.

:::image type="content" source="media/dynamic-pos-days-scenario-3.png" alt-text="Timeline for example scenario 3.":::
