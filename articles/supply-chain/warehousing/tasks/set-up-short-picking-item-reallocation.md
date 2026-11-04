---
title: Set up short picking item reallocation
description: Learn how to enable warehouse workers to quickly find alternative locations if there isn't sufficient inventory at the location they've been directed to.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSWorkException, WHSWorker
ms.topic: how-to
ms.date: 11/04/2026
ms.custom:
  - bap-template
---

# Set up short picking item reallocation

[!INCLUDE [banner](../../includes/banner.md)]

When there's not enough inventory at the location that a warehouse worker is directed to pick from, the situation is known as a *short pick*. Item reallocation lets the worker quickly find an alternative location so that picking can continue. This article explains how to set up item reallocation for short picks.

Item reallocation is controlled by a *work exception* of the *Short pick* type. Each work exception defines how the system responds when a worker reports the exception on the Warehouse Management mobile app. Manual reallocation also requires that the individual worker is allowed to use it.

## Item reallocation options

The **Item reallocation** field on a work exception provides the following options:

- *None* – No reallocation occurs. The worker must resolve the shortage another way. This option is the default.
- *Automatic* – Location directives determine whether the goods are available at another location. If they are, the work is updated, and the worker is directed to the alternative location.
- *Manual* – The worker selects from a list of locations that have unreserved quantities of the item.
- *Automatic and manual* – The system first tries automatic reallocation. If it can't reallocate the work automatically, and locations that have unreserved quantities are available, the worker is prompted to select a location.

Consider defining several work exceptions that have different item reallocation policies. Workers can then choose the exception that fits the shipment that they're processing.

### Requirements for manual reallocation

Both the *Manual* and *Automatic and manual* options require that the worker has the **Allow manual item reallocation** option turned on. If the worker doesn't have this permission, no reallocation occurs at all. In other words, if you select *Automatic and manual* for a worker who isn't allowed to use manual reallocation, that worker doesn't fall back to automatic reallocation.

### Supported work order types

Item reallocation applies only to some work order types:

- Automatic reallocation is supported for *Replenishment*, *Raw material picking*, *Sales orders*, and *Transfer issue*.
- Manual reallocation is supported for *Raw material picking*, *Sales orders*, *Transfer issue*, and *Outbound shipment order*.

You can reallocate replenishment work automatically, but not manually. If the work order type doesn't support the option that you select, the system processes the work as though you didn't set up reallocation.

## Create a work exception for short picking

Create a work exception that workers report when they find a short pick, and set its item reallocation policy. Follow these steps:

1. Go to **Warehouse management** > **Setup** > **Work** > **Work exceptions**.
1. On the Action Pane, select **New** to add a row to the grid.
1. Set the following fields for the new row:

    - **Work exception code** – Enter a unique identifier for the exception. Workers see this code and its description when they report an exception, so use a name that describes the situation, such as *Short pick manual*. You can't change the code after you save the row.
    - **Description** – Enter a short description of when the exception should be used, such as *Short picking - item not available*.
    - **Exception type** – Select *Short pick*. You can't change the type after you save the row, so ensure that you select the correct value before you save. The available types are *Work*, *Receiving*, and *Short pick*, but only *Short pick* supports item reallocation.
    - **Automatically create cycle counting** – Select this checkbox to have the system automatically create cycle counting work for the affected location. Counting the location confirms the actual on-hand quantity after a discrepancy is reported. This option is available for the *Work* and *Short pick* exception types.
    - **Adjust inventory** – Select this checkbox to have the system automatically adjust the on-hand quantity at the short-picked location to 0.
    - **Default adjustment type code** – Select the adjustment type code that defines how the adjustment is posted. Each adjustment type code specifies an inventory journal name and whether reservations are removed. If reservations are removed, the system releases the reservations on the short-picked order line so that the line can be reserved elsewhere. This field is required when you select **Adjust inventory**, and it's unavailable otherwise.
    - **Automatically decrement shipment or load** – Select this checkbox to have the system reduce the quantity on the related shipment or load by the quantity that couldn't be picked. Use this option when the shipment should go out with the reduced quantity instead of waiting for the full quantity.
    - **Suggest wave label reprint** – Select this checkbox to prompt the worker to void and reprint wave labels. Because the quantity on the shipment can change after a short pick, existing labels might no longer be accurate. Learn more in [Reprint and void wave labels](../reprint-and-void-wave-labels.md).
    - **Item reallocation** – Select the reallocation option to use, as described earlier in this article.

1. On the Action Pane, select **Save**.

> [!NOTE]
> The **Adjust inventory**, **Default adjustment type code**, **Suggest wave label reprint**, and **Item reallocation** fields are available only for exceptions of the *Short pick* type. If you change the exception type, the system resets these fields.

## Allow a worker to use manual item reallocation

All workers can use automatic reallocation. Turn on manual reallocation for each worker who needs it. This requirement helps you control which workers can see and pick from areas such as quarantine or bulk locations.

To allow a worker to use manual item reallocation, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Worker**.
1. On the Action Pane, select **Edit**, and then select the worker to set up.
1. On the **Users** FastTab, select the user account to set up.
1. On the **Work** FastTab, set the **Allow manual item reallocation** option to *Yes*.
1. On the Action Pane, select **Save**.

Learn more about the other settings that are available for each user account in [Mobile device user accounts](../mobile-device-work-users.md).

## Related information

- [Mobile device user accounts](../mobile-device-work-users.md)
- [View and manage the work exceptions log](../work-exceptions-log.md)
- [Reprint and void wave labels](../reprint-and-void-wave-labels.md)
- [Cycle counting](../cycle-counting.md)
