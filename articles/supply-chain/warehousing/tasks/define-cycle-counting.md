---
title: Define cycle counting
description: Learn how to set up cycle counting for a warehouse, including counting work priority, mobile device menus, thresholds, and cycle count plans.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSRFMenuItemCycleCount, WHSCycleCountThreshold, WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSParameters, WHSRFMenu, WHSRFMenuItem
ms.topic: how-to
ms.date: 10/09/2026
ms.custom:
  - bap-template
---

# Define cycle counting

[!INCLUDE [banner](../../includes/banner.md)]

Cycle counting is a warehouse process that you can use to audit on-hand inventory items without having to perform a full physical inventory. To set up cycle counting, you configure the counting work priority, create a mobile device menu item that warehouse workers use to process counts, set up counting thresholds that trigger counts when locations become empty, and create cycle count plans that schedule counts for specific items or locations.

A warehouse manager typically performs these tasks.

## Set the priority of counting work

Cycle counting work competes with other warehouse work types for worker attention. By setting a lower priority number, you raise the priority of counting work so it gets processed before other work types. To configure the default priority, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Warehouse management parameters**.
1. Select the **Cycle counting** tab.
1. In the **Default cycle count work priority** field, enter a number. A lower number means higher priority. For example, if picking work has a priority of 50, set cycle counting to 30 to ensure counts are processed first.
1. On the Action Pane, select **Save**.
1. Close the page.

## Enable the mobile device

To allow warehouse workers to process cycle counting from a mobile device, create a menu item that handles both picking and counting work. The menu item uses work classes to determine which types of work are presented to the worker. To set up a mobile device menu item for cycle counting, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Menu item name** – Enter a unique identifier for the menu item.
    - **Title** – Enter the name that workers see on the mobile device.
    - **Mode** – Select *Work*.
    - **Use existing work** – Set to *Yes*. When this option is set to *Yes*, the system looks for existing work when the mobile device menu item is used.
    - **Directed by** – Select *System directed*. The system directs the warehouse worker to open work in the order defined by the work classes and priority.
1. Expand the **Work classes** FastTab. Work classes control which types of work this menu item can process. Add the work classes you want workers to handle (for example, one for cycle counting and one for picking):
    1. Select **New**.
    1. In the **Work class ID** field, select the cycle counting work class.
    1. Select **New**.
    1. In the **Work class ID** field, select the picking work class.
1. On the Action Pane, select **Save**.
1. Close the page.

After you create the menu item, add it to a mobile device menu so workers can access it:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu**.
1. Select the menu where you want to add the item.
1. Select **Edit**.
1. Select the arrow to add the menu item you just created to the menu.
1. On the Action Pane, select **Save**.

## Create a counting threshold

Counting thresholds let you automatically trigger cycle counting work when inventory at a location falls to zero or below a specified level. For example, you can create a threshold that generates a count whenever a location becomes empty after a pick. To create a counting threshold, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Cycle counting** > **Cycle count thresholds**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Cycle counting threshold ID** – Enter a unique identifier for the threshold.
    - **Description** – Enter a description that explains what triggers this threshold.
    - **Process cycle counting immediately** – Set to *Yes* to create cycle counting work as soon as the threshold is reached. When set to *No*, the work is created the next time the threshold processing batch job runs.
1. On the Action Pane, select **Save**.
1. Select **Select locations** to define which locations this threshold applies to:
    1. In the **Criteria** field, select the locations or location criteria to include.
    1. Select **OK**.
1. Close the page.

## Create a cycle count plan

Cycle count plans schedule recurring counts for specific items or locations at regular intervals. For example, you can plan counts every five days for high-value items in a specific zone. To create a cycle count plan, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Cycle counting** > **Cycle count plans**.
1. On the Action Pane, select **New**.
1. Set the following fields:
    - **Cycle counting plan ID** – Enter a unique identifier for the plan.
    - **Description** – Enter a description that explains the purpose of this plan.
    - **Maximum number of cycle counts** – Enter the maximum number of cycle count work records that this plan can create in a single run.
    - **Days between cycle counting** – Enter the number of days between counting runs. For example, if you enter *5*, cycle counting work is created every five days. However, if you process cycle counting work on day three, the next count is created five days after that processing date (day eight), not five days after the original schedule.
1. On the Action Pane, select **Save**.
1. Select **Select locations** to define which warehouse locations this plan covers:
    1. In the **Criteria** field, select the locations or location criteria to include.
    1. Select **OK**.
1. To add item-level criteria that further narrow which products are counted, select **New** in the plan lines grid and set the following fields:
    - **Sequence number** – Enter a number that determines the processing order. Lower numbers are processed first. The value must be greater than 0 (zero).
    - **Description** – Enter a description for this plan line.
1. On the Action Pane, select **Save**.
1. Select **Define product query** to specify which items this plan line covers:
    1. In the **Criteria** field, select the item or item criteria to include.
    1. Select **OK**.
1. Close the page.

## Related information

- [Cycle counting](../cycle-counting.md)
- [Cycle counting example scenarios](../cycle-counting-scenarios.md)
- [Partial location cycle counting](../partial-location-cycle-counting.md)
- [Set up work templates for partial location cycle counting](define-partial-location-cycle-counting-process.md)
