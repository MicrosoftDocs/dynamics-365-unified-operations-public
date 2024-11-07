---
title: Limit time series edits with time fences
description: Learn how to create and use time fences, which let demand planning managers define rules that prevent users from manually editing time series values that are associated with a specified time span.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 11/05/2024
ms.custom: 
  - bap-template
---

# Limit time series edits with time fences

[!include [banner](../includes/banner.md)]

*Time fences* let demand planning managers define rules that prevent users from manually editing time series values that are associated with a specified time span. They ensure that agreed-upon plans remain intact and unchanged during specified periods.

For example, users might be prevented from editing specific time series values that fall within the current month. However, they can still edit values for the previous month or the next month. Every time fence uses the bucket size of the time series to establish a time span that starts in the current period and extends a fixed number of periods into the future.

Time fences are defined as logical expressions and apply to all time series cells where the expression is true. For example, you might make a time fence that lasts two months, and that applies to product ID *K0001* in color *Red* for all time series that use *Monthly* time buckets.

Time fences are both flexible and easy to maintain. Managers create time fence rules based on the dimensions that are available in each plan. For example, a single product can be set up so that different time fences apply to each store or geographical location. Time fence rules can also apply based on each user's role. For example, a role-based time fence rule might allow managers to edit a forecast in a period that can't be edited by planners.

## Time fence example

The following screenshot shows an example of a time series where two time fences apply. The time fences are represented by cells that show a lock symbol. This symbol indicates that the cells are locked. Therefore, the current user can't edit the values in them. However, the user can still edit the values in all unlocked cells. The following time fences apply here:

- Warehouse location name (**Warehouse location**) = *Store 1 US*; Time bucket = *Monthly*; Size = *Current period + 2 Time buckets*
- Product variant name (**Product**) = *Car Audio Unit-200, Car Audio Unit-500, Car Audio 65-Silver*; Time bucket = *Monthly*; Size = *Current period + 4 time buckets*

:::image type="content" source="media/time-fence-example.png" alt-text="Screenshot that shows an example of two time fences on the Timeline FastTab of the Forecast page." lightbox="media/time-fence-example.png":::

## Manage time fences

To view, create, edit, or delete a time fence, follow these steps.

1. On the navigation pane, select **Configuration** \> **Time fences**.

    The **Active time fence rules** page shows a list of active time fences. For each time fence, you can review the name, conditions, role, and other settings.

1. Follow one or more of these steps as required:

    - To create a new time fence, select **New** on the Action Pane.
    - To edit an existing time fence, select the link in the **Name** column.
    - To delete a time fence, select the row for it, and then, on the Action Pane, select **Delete**.
    - To view and edit deactivated time fences, select the **Active time fence rules** heading, and then select **Deactivated time fence rules** in the dropdown list.

1. If you chose to create or edit a time fence in the previous step, a tabbed window appears. On the **Summary** tab, set the following fields:

    - **Name** – Enter a name for the time fence.
    - **Description** – Enter a short description of the time fence.
    - **Owner** – Select the user account that owns the time fence record.
    - **Active** – Select whether the time fence should be active.

1. On the **Conditions** tab, define the conditions under which the time fence applies. Use the **Add condition** and **Delete** (trashcan) buttons to add or remove rows as required. The rows are combined by using an *AND* operator. Therefore, the time fence locks only cells where the condition in *every* row is true. For each row, set the following fields:

    - **Table** – Select the data table that provides the cell value to compare.
    - **Column** – For the selected table, select the column that provides the cell value to compare.
    - **Operator** – Select the logic to apply to test the cell value against the row value. For example, select *equals*, *greater than*, or *less than*.
    - **Value** – Enter a comma-separated list of values to compare the cell value to. You can either select among available values in a dropdown list or enter custom values. If you specify more than one value, the values are combined by using an *OR* operator. Therefore, the condition in the row is true for every time series cell that matches any one of the specified values.

1. On the **Time fence horizon** page, define the time span that the time fence applies to. The time span always starts in the time bucket that includes the current date. It then extends a fixed number of time buckets into the future. Set the following fields:

    - **Time buckets** – Specify the size of the time buckets that you want to use to define the time span. The time fence applies only to time series that also use this time bucket size. The system doesn't convert between time bucket sizes. For example, if you select *Monthly* here, your rule doesn't apply to time series that use *Weekly* time buckets (even though a month is about four weeks long).
    - **Current period +** – Specify the total number of time buckets, after the current one, to include in the time fence. The time fence always applies to the current time bucket. Therefore, if you want to include only the current time bucket in the time fence, set this field to *0* (zero). To include only the current time bucket and the next one, set this field to *1*.

    The **Example** area shows the time fence that results from your settings on this page.

1. On the **Role** page, select the user security roles that the time fence applies to.

## Overlapping time fences

In situations where time fences overlap, the more permissive condition applies. Here are some examples:

- A time fence for *all users* prevents a specific cell from being edited, but the time fence for the *manager* user role allows the cell to be edited. In this case, a user who has the *manager* role is allowed to edit the cell.
- A time fence of four months is set for location 1, but a time fence of two months is set for product 00001. In this case, the time fence for product 0001 at location 1 is two months.
