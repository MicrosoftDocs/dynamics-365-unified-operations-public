---
title: Limit automatic time series updates with time freezes
description: Learn how to create and use time freezes, which let demand planning managers define rules that prevent the system from automatically updating time series values that are associated with a specified time span.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 09/09/2025
ms.custom: 
  - bap-template
---

# Limit automatic time series updates with time freezes

[!include [banner](../includes/banner.md)]

*Time freezes* let planners define rules that prevent the system from automatically updating selected cells in existing time series when a forecast gets recalculated (such as when you use [rolling forecasts](rolling-forecasts.md) or when you manually rerun a forecast to update an existing time series). Time freezes are similar to [time fences](time-fences.md), which are used to prevent users from *manually* editing certain time series values. However, time freezes only prevent *automated* updates that would otherwise occur when you rerun a forecast; users can still edit those values manually in the time series.

Unlike time fences (which apply to all time series that match the time fence logic), you must explicitly configure each relevant *Forecast* and *Forecast with signals* step to use the time freezes that should apply to it. You can assign any number of time freezes to each step, and you can also assign no time freezes at all. If you don't assign any time freezes to a step, then the step won't use any time freeze rules.

For example, the system might be prevented from updating specific forecast values that fall within the next three months. However, the system can still update values for the previous month or for four months from now. Time freezes use the bucket size of the time series to establish a time span that starts in the current period and extends a fixed number of periods into the future.

There are two types of time freezes:

- **Time freeze rules** – Time freeze rules are defined as logical expressions. For example, you could create a time freeze rule that lasts two months and applies to product ID *K0001* in color *Red*. The rule would then apply for all *Forecast* and *Forecast with signals* steps that have that time freeze assigned.
- **Freeze manual adjustments** – This type of time freeze is a simple on/off setting that you can enable for each *Forecast* and *Forecast with signals* step. When it's enabled, the system prevents automatic updates to any time series cells that have been manually adjusted by a user. No rules are required.

## Manage time freeze rules

To view, create, edit, or delete a time freeze rule, follow these steps.

1. On the navigation pane, select **Configuration** \> **Time freezes**.

    The **Active time freeze rules** page shows a list of active rules. For each rule, you can review the name, conditions, and other settings.

1. Follow one or more of these steps as required:

    - To create a new time freeze rule, select **New** on the Action Pane.
    - To edit an existing time freeze rule, select the link in the **Name** column.
    - To delete a time freeze rule, select the row for it, and then, on the Action Pane, select **Delete**.
    - To view and edit deactivated time freeze rules, select the **Active time freeze rules** heading, and then select **Inactive time freeze rules** in the dropdown list. Other views are also available here, including views for viewing only daily, monthly, or weekly time freeze rules.

1. If you chose to edit a time freeze rule in the previous step, a tabbed window appears. If you choose to create a new time freeze, then a wizard launches, which offers similar settings. On the **Summary** edit tab (or **Get started** wizard page), set the following fields:

    - **Name** – Enter a name for the rule.
    - **Description** – Enter a short description of the rule.
    - **Owner** – Select the user account that owns the time freeze rule record.
    - **Active** – Select whether the rule should be active. Inactive rules have no effect, even when explicitly assigned to step. (This option is only shown on the **Summary** edit tab. In the wizard, you can set this option on the **Review and finish** page.)

1. On the **Conditions** edit tab (or **Add conditions** wizard page), define the conditions under which the rule applies. Use the **Add condition** and **Delete** (trashcan) buttons to add or remove rows as required. The rows are combined by using an *AND* operator. Therefore, the rule locks only cells where the condition in *every* row is true. For each row, set the following fields:

    - **Table** – Select the data table that provides the cell value to compare.
    - **Column** – For the selected table, select the column that provides the cell value to compare.
    - **Operator** – Select the logic to apply to test the cell value against the row value. For example, select *equals*, *greater than*, or *less than*. There's also a *Select all* operator, which matches all values in the column (learn more in [Using the select all operator](time-fences.md#select-all)).
    - **Value** – Enter a comma-separated list of values to compare the cell value to. You can either select among available values in a dropdown list or enter custom values. If you specify more than one value, the values are combined by using an *OR* operator. Therefore, the condition in the row is true for every time series cell that matches any one of the specified values. The **Value** field is disabled when you use the *Select all* operator.

1. On the **Time freeze horizon** edit tab or wizard page, define the time span that the time freeze rule applies to. The time span always starts in the time bucket that includes the current date. It then extends a fixed number of time buckets into the future. Set the following fields:

    - **Time buckets** – Specify the size of the time buckets that you want to use to define the time span. The time freeze rule can only be used with forecast profiles that also use this time bucket size. The system doesn't convert between time bucket sizes. For example, if you select *Monthly* here, your rule won't be available to forecast models in profiles that use *Weekly* time buckets (even though a month is about four weeks long).
    - **Current period +** – Specify the total number of time buckets, after the current one, to include in the time freeze rule. The rule always applies to the current time bucket. Therefore, if you want to include only the current time bucket in the rule, set this field to *0* (zero). To include only the current time bucket and the next one, set this field to *1*.

    The **Example** area shows the time freeze rule that results from your settings on this page.

1. On the **Review and finish** wizard page (which isn't shown when you edit an existing rule), review the settings that you made in the previous steps and set the **Active** option as needed. If everything looks correct, select **Review and Finish** to create the rule.

## Add a time freeze rule to a forecast profile

As mentioned, you must explicitly configure each relevant *Forecast* and *Forecast with signals* step to use the time freeze rules that should apply to it. To do this, follow these steps:

1. Create the time freeze records that you want to use, as described in the previous sections of this article.
1. Create or open a relevant forecast profile as described in [Work with forecast profiles](forecast-profiles.md).
1. On the **Forecast model** tab, crate or select the step that you want to add a time freeze rule to. The step must be a *Forecast* or *Forecast with signals* step. (Learn more in [Design forecast models](design-forecast-models.md).) If you're editing an existing step, open the **Actions** menu for the step and then select **Settings**.
1. In the Freeze values section, select the **Enable time freeze** check box.
1. Select the **Use time freeze** rules radio button.
1. Use the **Time freeze rules** field to search for and select the time freeze rules that you want to apply to the step.

## Freeze manual adjustments for a selected forecast profile

To prevent the system from automatically updating any time series cells that have been manually adjusted by a user, use the following procedure. You don't need to create any time freeze rules to use this feature.

1. Create or open a relevant forecast profile as described in [Work with forecast profiles](forecast-profiles.md).
1. On the **Forecast model** tab, crate or select the step that you want to add a time freeze rule to. The step must be a *Forecast* or *Forecast with signals* step. (Learn more in [Design forecast models](design-forecast-models.md).) If you're editing an existing step, open the **Actions** menu for the step and then select **Settings**.
1. In the Freeze values section, select the **Enable time freeze** check box.
1. Select the **Freeze manual adjustments** rules radio button.
