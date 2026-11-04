---
title: Set up work templates for partial location cycle counting
description: Learn how to create a work template that breaks cycle counting work into item lines, so that workers count only selected products at a location.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSWorkTemplateTable, WHSWorkTemplateLineGroup
ms.topic: how-to
ms.date: 11/04/2026
ms.custom:
  - bap-template
---

# Set up work templates for partial location cycle counting

[!INCLUDE [banner](../../includes/banner.md)]

By default, cycle counting work is created for a whole location, and the worker must count everything that's on hand there. Partial location cycle counting narrows the count to specific products, so the warehouse manager can reduce review overhead, help prevent consolidation mistakes, and save time.

The setting that makes this behavior possible is the *work line break* on the work template that the cycle count plan references. Work line breaks split the cycle counting work into one line per item number, or per product variant number. Without them, the plan creates a single work line for the location, and the partial count can't occur.

This article explains how to build that work template. A warehouse manager typically performs this task.

## Prerequisites

Before you begin, ensure that you meet the following prerequisites:

- The warehouse is enabled for warehouse management processes (WMS).
- A work class that has a *Counting* work type exists. You can create work classes at **Warehouse management** > **Setup** > **Work** > **Work classes**.
- A mobile device menu item for cycle counting exists, and the **Display item number** option is set to *Yes* for it. Workers are then prompted to record counting information only for the items on the counting lines. Learn more in [Define cycle counting](define-cycle-counting.md).

## Create the work template

The work template controls how cycle counting work is created and which workers can process it. To create a work template for cycle counting, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Work** > **Work templates**.
1. In the **Work order type** field, select *Cycle counting*.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Sequence number** – Enter a number that determines the order in which the system evaluates the available work templates. The system evaluates templates from the smallest number to the largest number. Give specific templates a low sequence number so that the system evaluates them before more general templates. You can change the sequence later if necessary.
    - **Work template** – Enter a unique identifier for the template.
    - **Work template description** – Enter a description that explains when this template applies.
    - **Work pool ID** – Optional. Select a work pool if you want to group the counting work together with other work for reporting or filtering.
    - **Work priority** – Enter a number. A lower number means higher priority.
1. On the Action Pane, select **Save**.
1. On the **Work template details** grid toolbar, select **New**, and then set the following fields:
    - **Work type** – Select *Counting*.
    - **Work class ID** – Select the work class that your cycle counting mobile device menu item uses. Learn more in [Create a work class](create-work-class.md).
1. On the Action Pane, select **Save**.

## Define the work line breaks

Work line breaks determine the level of detail for the counting work lines that are created. Because the guided counting operation on the mobile device follows this level of detail, the work line breaks are what let a worker count individual products instead of a whole location. To define them, follow these steps:

1. Select the work template that you created.
1. On the **Work template details** grid toolbar, select **Work line breaks**.
1. On the Action Pane, select **New**, and then set the following fields:
    - **Sequence number** – Enter a number. The system applies group by fields from the smallest number to the largest number.
    - **Group by field** – Select *Item number*. The system creates a separate counting work line for each item at the location.
1. If you want workers to count each product variant separately, add another line and then set the following fields:
    - **Sequence number** – Enter a number that's higher than the number that you entered for the *Item number* row.
    - **Group by field** – Select *Product variant number*.
1. On the Action Pane, select **Save**.
1. Close the page.

The following rules apply to work line breaks:

- You can group by *Product variant number* only if you also group by *Item number*.
- The *Product variant number* row must have a higher sequence number than the *Item number* row.
- You can't delete the *Item number* row while a *Product variant number* row exists.

## Next steps

Reference the work template from a cycle count plan, and use the **Select locations** query and the product queries on that plan to control which locations and products are counted. Learn more in [Define cycle counting](define-cycle-counting.md).

When you process the plan, the **Partial cycle count** field is selected for the cycle counting work that is created, and multiple work lines are created according to the work line breaks that you defined. For the limitations that apply to this process, learn more in [Partial location cycle counting](../partial-location-cycle-counting.md).

## Related information

- [Cycle counting](../cycle-counting.md)
- [Partial location cycle counting](../partial-location-cycle-counting.md)
- [Define cycle counting](define-cycle-counting.md)
- [Cycle counting example scenarios](../cycle-counting-scenarios.md)
- [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md)
