---
# required metadata

title: Coverage time fence
description: This topic describes how to set up a coverage time fence when you are using Planning Optimization. The coverage time fence indicates your planning horizon and limit.
author: ChristianRytt
manager: tfehr
ms.date: 01/18/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2021-01-18
ms.dyn365.ops.version: 10.0.17
---

# Coverage time fence

When you are using the Planning Optimization Add-in for Supply Chain Management, the only type of time fence currently supported is the *coverage time fence*, which indicates your planning horizon and limit.

The coverage time fence allows planners to define the planning horizon (coverage time fence in days) and exclude supply and demand that falls outside of that horizon. This helps to prevent noise caused by supply suggestions that you don't need to react on for months. Examples include next year's forecast, or customer orders placed way beyond the normal lead time.

The coverage time fence is the number of days from today's date (or a more precise planning run time) after which supply and demand are excluded.

To avoid delays, you must ensure that the time fence is longer that the total lead time. The default system value is 100 days.

## Set up coverage time fences

You can specify coverage time fences on any of the following pages:

- Coverage groups (where you can set a default coverage time fence for each group)
- Item coverage (where you can overwrite the coverage time fence inherited from the coverage group)
- Master plans (where you can overwrite the coverage time fences inherited from the coverage group and/or item coverage settings.)

### Set a coverage time fence for coverage groups

When you assign a coverage time fence for a coverage group, that setting will apply to all items (products) that are part of that group, though you can overrule the setting for specific items or specific master plans.

To assign a coverage time fence to a coverage group:

1. Go to **Master planning \> Setup \> Coverage \> Coverage groups**.
1. Expand the **General** FastTab.
1. Specify the desired value for **Coverage time fence (days)**.

### Set a coverage time fence for a specific item

All items (products) belong to a coverage group. There is a default coverage group that applies to all items, but you can also assign a custom group to each item as needed. Each item inherits its coverage time fence from the coverage group it is assigned to, but you can overrule this for specific items as needed.

To assign a coverage time fence for a specific item:

1. Go to **Product information management \> Products \> Released products**.
1. Select a product in the grid.
1. On the Action Pane, open the **Plan** tab and, from the **Coverage** group, select **Item coverage**.
1. The **Item coverage** page opens. On the **Overview** tab, select or create a row for the site where you want to set a coverage time fence.
1. Open the **General** tab to open settings for your selected site.
1. Select the **Override coverage group settings** check box.
1. Set **Coverage period** to the number of days to use as the coverage time fence for this item.  <!-- KFM: The Coverage period setting is read-only for me. There is also a setting here called "Coverage time fence (days)", so why don't we use that one? There are several settings here, are all of them actually relevant for adjusting the time fence? -->

### Set a coverage time fence for a specific master plan

You can assign a coverage time fence at the master plan level. This establishes the number of days the master planning calculation will cover for this master plan. This setting overrules any coverage time settings otherwise established for each relevant item and coverage group.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a master plan from the list pane (or create a new one).
1. Expand the **Time fences in days** FastTab.
1. Set **Coverage** to *Yes* and then enter the number of days into the field located below this slider.

## Coverage time fence considerations

As you are setting up your coverage time fences, consider the following points:

- Coverage time fences only affect input data for master planning. In case of delays, the resulting planned orders might have a date that is after today's date plus the coverage time fence.
- The coverage time fence is specified in calendar days. Calendars set up with working days do not affect the time fence calculation. For example, a week is always considered to be 7 days even when weekends are set up as closed days in the working time calendar.
- Requirement transactions will not be generated for any supply/demand that falls outside of the coverage time fence.
- If approved supply and demand falls outside of the coverage time fence, then it will not be loaded into the engine. Consequently, it will not trigger any replenishment and delays will not be calculated. At the same time, it should not be wiped from the system.
- Safety stock quantity variations (from minimum keys) will be ignored if they fall beyond the coverage time fence.
- Intercompany demand will be ignored if the calculated requested ship date is not within the coverage time fence. Note that with built-in master planning, intercompany demand is not limited by the coverage time fence.
- Demand forecast will be ignored if the budget date is not within the coverage time fence. Note that with built-in master planning, demand forecast is not limited by the coverage time fence.
- Planning Optimization is time-zone aware. It considers the time zone at the supply and demand sites and also considers the time of the run. For example, if master planning is triggered at 11 am on October 15 from a site in Denmark (GMT +1h time zone) using a coverage time fence of 10 days, then demand and supply from a site in Seattle (GMT -8h time zone) is included until 2 am on October 25 (10 24-hour days, minus the time zone difference of 9 hours). Note that the built-in master planning engine only considers the date of the time fence, so the result can differ.
