---
title: Limit time series edits with time fences
description: XXXX
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

For example, users might be prevented from editing time series values that fall within the current month, though they can still edit values for last month or next month. Each time fence establishes a time span that starts at the current time period (using the bucket size of the time series) and extending a fixed number of periods into the future.

Time fences are both flexible and simple to maintain. Managers create time fence rules based on the dimensions available in each plan. For example, a single product could be set up with different time fences for each store or geographical location. Time fence rules can also apply based on each user's role. For example, a role-based time fence rule could allow managers to edit a forecast in a period that can't otherwise be edited by planners.

## Create a time fence

To create a time fence, follow these steps.

1. On the navigation pane, select **Configuration** \> **Time fences**.
1. On the Action Pane, select **New**.
1. On the **Conditions** page, establish the conditions where the time fence applies. Use the **Add condition**  and **Delete** (trashcan) buttons to add or remove rows, as needed. The rows are combined using an AND operator, which means only cells where *all* of the rows listed here apply will be locked by the time fence. Make the following settings for each row:
    - **Table** – Select the data table that provides the value to test.
    - **Column** – Select the column from the selected table that provides the value to test.
    - **Operator** – Choose the logic to apply (such as *equals*, *greater than*, or *less than*).
    - **Value** – Select the value to test. This field either provides a drop-down list of available values or allows you enter a value, depending on the table and column you've selected. If you add more than one value here, then the values are combined with and *OR* operator, which means that the row will apply to any time series cell that contains any one of these values.

1. On the **Time fence horizon** page, establish the time span where the fence applies. It always starts at the time bucket that includes the current day and extends a fixed number of time buckets into the future. Make the following settings:
    - **Time buckets** – Specify the size of the time buckets you want to use to define the time span. The time fence you are creating will onl apply to time series that also use this time bucket. It system won't convert between time bucket sizes so, for example, if you select *Monthly* here, your rule won't apply to time series that use *Weekly* time buckets (even though a month is about four weeks).
    - **Current period** – Specify the total number of time buckets (after the current one) to include in the time fence. The time fence always applies to the current time bucket, so set this to 0 (zero) to include only the current one. Set it to 1 to include both the current and next time buckets.

    The **Example** display illustrates the time fence that results from your settings on this page.

1. On the **Role** page, choose the user security roles where the time fence applies. In situations where more than one role-based time fence applies for the current user for a certain cell in a time series, the more permissive condition applies. For example, if the user has the *manager* user role, and a time fence for *all users* would block a certain cell from being edited, while the time fence for the *manager* role allows it, the user will be permitted to edit the cell.

