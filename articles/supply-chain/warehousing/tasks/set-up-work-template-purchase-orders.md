---
title: Set up a work template for purchase orders
description: Learn how to set up a work template that controls how received items are put away, including how to create the header, query, and work template lines.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSWorkTemplateTable
ms.topic: how-to
ms.date: 11/04/2026
ms.custom:
  - bap-template
---

# Set up a work template for purchase orders

[!INCLUDE [banner](../../includes/banner.md)]

When warehouse workers receive items against a purchase order, a work template controls how they put those items away. This article explains how to set up a work template for purchase order putaway.

A work template defines the set of instructions that a warehouse worker receives on a mobile device. Each work template is for a single work order type, and it consists of a header and one or more lines. The header controls when the template is used and what defaults the resulting work gets. The lines represent the physical tasks that make up the work, and they're always defined in pick and put pairs.

The template described here creates a simple pair of instructions: pick the received items up from the location where they were registered, and put them away in a storage location. The work template doesn't determine the put location. A location directive determines the put location when you create the work. Learn more in [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md).

This procedure is intended for the warehouse manager.

## Prerequisites

Before you begin, ensure that a work pool ID exists. Work pool IDs organize work into groups, so warehouse supervisors can monitor and release related work together. Create one that represents your inbound putaway work, such as *Inbound*, by going to **Warehouse management** > **Setup** > **Work** > **Work pools**.

## Create a work template header

The header identifies the template, sets its priority relative to other templates for the same work order type, and defines the defaults that apply to the work the template creates.

1. Go to **Warehouse management** > **Setup** > **Work** > **Work templates**.
1. In the **Work order type** field, select **Purchase orders**.
1. Select **New**.
1. In the **Sequence number** field, enter a number. This number determines the order in which the system evaluates the available work templates. The system evaluates templates from the smallest number to the largest number. Give specific templates a low sequence number so that the system evaluates them before more general templates. You can change the sequence later if necessary.
1. In the **Work template** field, enter a unique identifier for the template.
1. In the **Work template description** field, enter a description.
1. In the **Work pool ID** field, select the work pool that the system should group inbound putaway work into. This value becomes the default work pool for any work that this template creates.
1. In the **Work priority** field, enter *1*. This value indicates the importance of the work, and it becomes the default priority for any work that this template creates.
1. Leave the **Automatically process** option unselected. This option is intended for work that the system completes as soon as it creates the work, without a worker. Don't use this option for purchase order putaway, because a worker registers and puts away the received items by using a mobile device.
1. On the Action Pane, select **Save**. You must save the header before the **Edit query** button becomes available.

The **Valid** check box remains cleared until the template contains everything that's required. The system selects it automatically after you add a matching pick and put pair and save the template again.

## Set up the query for the work template

The query controls when the template is used. Any work template whose query matches the work that you're creating is a candidate. The sequence number decides which candidate wins. The following steps limit the template to a single warehouse.

1. Continue working with the template that you created.
1. On the Action Pane, select **Edit query**.
1. On the **Range** tab of the query editor, select **Add**.
1. Leave the **Table** column of the new row set to *Temporary work transactions*.
1. In the **Field** column of the new row, select *Warehouse*.
1. In the **Criteria** column, select the warehouse that the template applies to. The warehouse must be enabled for warehouse management processes (WMS). In the standard demo data, warehouse *24* is enabled for these processes.
1. Select **OK**.
1. If you're prompted to confirm the change, select **Yes**.

If you want to create a separate work record for each order number or another grouping, use the **Work header breaks** button instead of or in addition to the query. Learn more in [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md).

## Set up the work template lines

The work template lines are the tasks that the worker performs. Create pick and put lines as pairs, and ensure both lines in a pair use the same work class.

1. Continue working with the template that you created.
1. In the **Work template details** grid toolbar, select **New**, and then set the following fields:
    - **Work type** – Select *Pick*.
    - **Work class ID** – Select the work class that represents purchase order putaway. The work class controls which workers can process the line, because each mobile device menu item is restricted to specific work classes. The work class is applied from the template when the work is created, and you don't set it on individual work order lines. Learn more in [Create a work class](create-work-class.md).

1. Add another row to the **Work template details** grid and make the following settings for it:
    - **Work type** – Select *Put*.
    - **Work class ID** – Select the same work class that you selected for the pick line.

1. On the Action Pane, select **Save**.

The **Valid** check box is now selected, and the template is ready to use.

### About the Directive code field

Each work template line also has a **Directive code** field. A directive code links a work template line to a specific location directive, so you can point different lines at different location directives. It's useful when a template has several put steps, such as a put to a staging location that is followed by a put to a final location.

For purchase order work templates, the last put line in the template must leave **Directive code** blank. If you set a directive code on it, the system shows the message *Field 'Directive code' cannot be set for this Work template line.* Because the template in this article has only one put line, that line is also the last put line, so its **Directive code** field stays blank. The location directive that matches the work order type, work type, and warehouse determines the put location. Learn more in [Set up a location directive for purchase order putaway](set-up-location-directive-purchase-order-put-away.md).

## Related information

- [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md)
- [Set up a location directive for purchase order putaway](set-up-location-directive-purchase-order-put-away.md)
- [Create a work class](create-work-class.md)
- [Dynamic work classification](../dynamic-work-classification.md)
