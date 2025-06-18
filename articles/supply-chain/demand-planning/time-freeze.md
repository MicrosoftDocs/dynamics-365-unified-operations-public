---
title: Limit time series updates with time freezes
description: Learn how to create and use time freezes, which let demand planning managers define rules that prevent the system from automatically updating time series values that are associated with a specified time span.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 11/05/2024
ms.custom: 
  - bap-template
---

# Limit time series updates with time freezes

[!include [banner](../includes/banner.md)]

<!-- KFM: This is a copy of the time fence article with freeze pasted in everywhere. Careful review and update still needed. -->

*Time freezes* let demand planning managers define rules that prevent the system from automatically updating existing time series when a forecast gets recalculated, such as when you use [rolling forecasts](rolling-forecasts.md) or when you manually rerun a forecast to update an existing time series. Time freezes are similar to [time fences](time-fences.md), which are used to prevent users from *manually* editing certain time series values. However, time freezes only prevent *automated* updates that would otherwise occur when you rerun a forecast; users can still edit those values manually in the time series.

For example, the system might be prevented from updating specific time series values that fall within the next three months. However, the system can still update values for the previous month or for four months from now. Time freezes use the bucket size of the time series to establish a time span that starts in the current period and extends a fixed number of periods into the future.

Time freezes are defined as logical expressions and apply to all time series cells where the expression is true. For example, you create a time freeze that lasts two months and applies to product ID *K0001* in color *Red* for all time series that use *Monthly* time buckets.

Time freezes are both flexible and easy to maintain. Managers create time freeze rules based on the dimensions that are available in each plan. For example, a single product can be set up so that different time freezes apply to each store or geographical location.

To view, create, edit, or delete a time freeze, follow these steps.

1. On the navigation pane, select **Configuration** \> **Time freezes**.

    The **Active time freeze rules** page shows a list of active time freezes. For each time freeze, you can review the name, conditions, and other settings.

1. Follow one or more of these steps as required:

    - To create a new time freeze, select **New** on the Action Pane.
    - To edit an existing time freeze, select the link in the **Name** column.
    - To delete a time freeze, select the row for it, and then, on the Action Pane, select **Delete**.
    - To view and edit deactivated time freezes, select the **Active time freeze rules** heading, and then select **Inactive time freeze rules** in the dropdown list. Other views are also available here, including views for viewing only daily, monthly, or weekly time freeze rules. <!-- KFM: No longer true? On my Aurora build, these does nothing and inactive time fences are shown in the Active time fence rules view. Remove this? -->

1. If you chose to edit a time freeze in the previous step, a tabbed window appears. If you choose to create a new time freeze, then a wizard launches, which offers similar settings. On the **Summary** edit tab (or **Get started** wizard page), set the following fields:

    - **Name** – Enter a name for the time freeze.
    - **Description** – Enter a short description of the time freeze.
    - **Owner** – Select the user account that owns the time freeze record.
    - **Active** – Select whether the time freeze should be active. (This option is only shown on the **Summary** edit tab. In the wizard, you can set this field on the **Review and finish** page.)

1. On the **Conditions** edit tab (or **Add conditions** wizard page), define the conditions under which the time freeze applies. Use the **Add condition** and **Delete** (trashcan) buttons to add or remove rows as required. The rows are combined by using an *AND* operator. Therefore, the time freeze locks only cells where the condition in *every* row is true. For each row, set the following fields:

    - **Table** – Select the data table that provides the cell value to compare.
    - **Column** – For the selected table, select the column that provides the cell value to compare.
    - **Operator** – Select the logic to apply to test the cell value against the row value. For example, select *equals*, *greater than*, or *less than*.
    - **Value** – Enter a comma-separated list of values to compare the cell value to. You can either select among available values in a dropdown list or enter custom values. If you specify more than one value, the values are combined by using an *OR* operator. Therefore, the condition in the row is true for every time series cell that matches any one of the specified values.

1. On the **Time freeze horizon** edit tab or wizard page, define the time span that the time freeze applies to. The time span always starts in the time bucket that includes the current date. It then extends a fixed number of time buckets into the future. Set the following fields:

    - **Time buckets** – Specify the size of the time buckets that you want to use to define the time span. The time freeze applies only to time series that also use this time bucket size. The system doesn't convert between time bucket sizes. For example, if you select *Monthly* here, your rule doesn't apply to time series that use *Weekly* time buckets (even though a month is about four weeks long).
    - **Current period +** – Specify the total number of time buckets, after the current one, to include in the time freeze. The time freeze always applies to the current time bucket. Therefore, if you want to include only the current time bucket in the time freeze, set this field to *0* (zero). To include only the current time bucket and the next one, set this field to *1*.

    The **Example** area shows the time freeze that results from your settings on this page.
