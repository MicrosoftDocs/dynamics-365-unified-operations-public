---
title: Limit time series edits with time fences
description: Learn how to create and use time fences, which let demand planning managers establish rules that prevent users from making manual edits to time series values associated with a specified time span. They ensure that agreed upon plans remain intact and unaltered during specified periods.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/14/2024
ms.custom: 
  - bap-template
---


# Limit time series edits with time fences

[!include [banner](../includes/banner.md)]

*Time fences* let demand planning managers establish rules that prevent users from making manual edits to time series values associated with a specified time span. They ensure that agreed upon plans remain intact and unaltered during specified periods.

For example, users might be prevented from editing certain time series values that fall within the current month, though they can still edit values for last month or next month. Each time fence establishes a time span that starts at the current time period (using the bucket size of the time series) and extends a fixed number of periods into the future.

Time fences are defined as logical expressions and apply to all time series cells where the expression is true. For example, you might make a time fence that lasts for two months and applies for product ID *K0001* of color *Red* for all time series that use *Monthly* time buckets.

Time fences are both flexible and simple to maintain. Managers create time fence rules based on the dimensions available in each plan. For example, a single product could be set up with different time fences for each store or geographical location. Time fence rules can also apply based on each user's role. For example, a role-based time fence rule could allow managers to edit a forecast in a period that can't otherwise be edited by planners.

## Time fence example

The following screenshot shows an example of a time series where two time fences apply. The time fence is indicated as cells that show a lock icon, which means that the current user can't edit the values in these locked cells. The user can still edit values in all of the unlocked cells. The following time fences apply here:

- Warehouse location name (**Warehouse location**) = *Store 1 US*; Time bucket = *Monthly*; Size = *4 Time buckets*
- Product ID (**Product**) = *K0001, K0005, K0010, K0011, K0012*; Time bucket = *Monthly*; Size = *2 time buckets*

<!--KFM: Add screen shot -->

## Manage time fence

To view, create, edit, or delete a time fence, follow these steps.

1. On the navigation pane, select **Configuration** \> **Time fences**.
1. The **Active time fence rules** page shows a list of each active time fence. You can review the name, conditions, role, and other settings for each time fence here.
    - To create a new time fence, select **New** on the Action Pane. This action opens a tabbed window where you can enter each setting
    - To edit a time fence, select it's link in the **Name** column. This action opens a tabbed window where you can edit each setting. The tabs are named and work the same way as they do when creating a new time fence.
    - To delete a time fence, select its row and then, on the Action Pane, select **Delete**.
    - To view and edit deactivated time fences, select the **Active time fence rules** heading to open a drop-down list and then select **Deactivated time fence rules**.
1. On the **Summary** tab, make the following settings.
    - **Name** – Enter a name for the time fence.
    - **Description** – Enter a short description for the time fence.
    - **Owner** – Select the user account that owns the time fence record.
    - **Active** – Choose whether the time fence should be active or not.
1. On the **Conditions** tab, establish the conditions where the time fence applies. Use the **Add condition**  and **Delete** (trashcan) buttons to add or remove rows, as needed. The rows are combined using an AND operator, which means only cells where *all* of the rows are true will be locked by the time fence. Make the following settings for each row:
    - **Table** – Select the data table that provides the cell value to compare.
    - **Column** – Select the column from the selected table that provides the cell value to compare.
    - **Operator** – Choose the logic to apply (such as *equals*, *greater than*, or *less than*) when testing a cell value against the row value.
    - **Value** – Enter a comma-separated list of values to compare the cell value to. This field either provides a drop-down list of available values and allows you enter custom values as needed. If you add more than one value, then the values are combined with and *OR* operator, which means that the row will be true for any time series cell that matches any one of these values.

1. On the **Time fence horizon** page, establish the time span where the fence applies. It always starts at the time bucket that includes the current day and extends a fixed number of time buckets into the future. Make the following settings:
    - **Time buckets** – Specify the size of the time buckets you want to use to define the time span. The time fence you are creating will onl apply to time series that also use this time bucket. It system won't convert between time bucket sizes so, for example, if you select *Monthly* here, your rule won't apply to time series that use *Weekly* time buckets (even though a month is about four weeks).
    - **Current period +** – Specify the total number of time buckets (after the current one) to include in the time fence. The time fence always applies to the current time bucket, so set this to 0 (zero) to include only the current one. Set it to 1 to include both the current and next time buckets.

    The **Example** display illustrates the time fence that results from your settings on this page.

1. On the **Role** page, choose the user security roles where the time fence applies. In situations where more than one role-based time fence applies for the current user for a certain cell in a time series, the more permissive condition applies. For example, if the user has the *manager* user role, and a time fence for *all users* would block a certain cell from being edited, while the time fence for the *manager* role allows it, the manager will be permitted to edit the cell.
