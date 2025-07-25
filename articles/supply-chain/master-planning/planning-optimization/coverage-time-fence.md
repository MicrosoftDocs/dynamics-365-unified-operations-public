---
title: Coverage time fences
description: Learn how to set up coverage time fences. A coverage time fence indicates your planning horizon and limit including definitions for coverage time fence levels.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqGroup, ReqItemTable, ReqPlanSched
ms.topic: how-to
ms.date: 07/21/2025
ms.custom:
- bap-template
---

# Coverage time fences

[!include [banner](../../includes/banner.md)]

This article describes how to set up *coverage time fences*. Planners can define the planning horizon (the coverage time fence in days), and exclude supply and demand that falls beyond that horizon. Therefore, coverage time fences help prevent "noise" caused by supply suggestions that don't require attention for months. Examples include next year's forecast and customer orders that are placed far beyond the normal lead time.

A coverage time fence is the number of days after today's date (or, more precisely, the date when you do the planning run) that supply and demand are excluded. To help avoid delays, you must ensure that the coverage time fence is longer that the total lead time. The default system value is 100 days.

You can specify a coverage time fence at each of the following levels:

- **Coverage group** – You can set a default coverage time fence for each coverage group.
- **Item coverage** – You can override the coverage time fence that is inherited from the coverage group that is assigned to an item.
- **Master plan** – You can override the coverage time fences that are inherited from the coverage group and item coverage settings.

The following sections explain how to specify a coverage group at each level.

## Set a coverage time fence for a coverage group

When you specify a coverage time fence for a coverage group, the setting applies to all items (products) that belong to that group. However, you can override the setting for specific items or specific master plans.

To specify a coverage time fence for a coverage group, follow these steps.

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. Select an existing coverage group in the list, or create a new coverage group.
1. On the **General** FastTab, set the **Coverage time fence (days)** field to the number of days that you want to use as the coverage time fence for the coverage group.

## Set a coverage time fence for a specific item

Every item (product) belongs to a coverage group. If no coverage group is explicitly assigned to an item, a default coverage group applies. Every item inherits a coverage time fence from its coverage group. However, you can override this time fence for specific items as you require.

To specify a coverage time fence for a specific item, follow these steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Select a product in the grid.
1. On the Action Pane, on the **Plan** tab, in the **Coverage** group, select **Item coverage**.
1. On the **Item coverage** page, on the **Overview** tab, select or create a row for the site where you want to set a coverage time fence.
1. Select the **General** tab to open the settings for the selected site.
1. Select the **Override coverage group settings** check box.
1. Set the **Coverage time fence (days)** field to the number of days that you want to use as the coverage time fence for the item.

## Set a coverage time fence for a specific master plan

You can specify a coverage time fence at the master plan level. In this way, you define the number of days that the master planning calculation covers for a master plan. This setting overrides any coverage time settings that are defined for each relevant item and coverage group.

To specify a coverage time fence for a specific master plan, follow these steps.

1. Go to **Master planning** \> **Setup** \> **Plans** \> **Master plans**.
1. Select an existing master plan in the list, or create a new master plan.
1. On the **Time fences in days** FastTab, set the **Coverage** option to *Yes*. Then, in the field under the option, enter the number of days that you want to use as the coverage time fence for the master plan.

## Considerations for coverage time fences

As you're setting up coverage time fences, consider the following points:

- Coverage time fences affect only input data for master planning. If delays occur, the resulting planned orders might have a date that is after today's date plus the coverage time fence.
- Coverage time fences are specified in calendar days. Calendars that use working days don't affect the time fence calculation. For example, a week is always considered seven days, even if weekends are set up as closed days in the working time calendar.
- Requirement transactions aren't generated for any supply and demand that falls outside the coverage time fence.
- If any approved supply and demand falls outside the coverage time fence, it isn't loaded into the engine. Therefore, it doesn't trigger any replenishment, and delays aren't calculated. Nevertheless, this supply and demand shouldn't be wiped from the system.
- Variations in safety stock quantities (from minimum keys) is ignored if they fall outside the coverage time fence.
- Intercompany demand is ignored if the requested ship date that is calculated isn't inside the coverage time fence. For the deprecated master planning engine, intercompany demand isn't limited by the coverage time fence.
- Demand forecasts are ignored if the budget date isn't inside the coverage time fence. For the deprecated master planning engine, demand forecasts aren't limited by the coverage time fence.
- Planning Optimization is time zone–aware. It considers the time zone at the supply and demand sites, and the time of the planning run. For example, master planning is triggered at 11 AM on October 15 from a site in Denmark (GMT+1 time zone), and a coverage time fence of ten days is used. In this case, supply and demand from a site in Seattle (GMT-8 time zone) is included until 2 AM on October 25 (which is ten 24-hour days after master planning was triggered, minus the time zone difference of nine hours). The deprecated master planning engine considers only the date of the time fence. Therefore, the result can differ.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
