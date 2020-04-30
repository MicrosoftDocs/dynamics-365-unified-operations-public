---
# required metadata

title: Planning Optimization fit analysis
description: This topic explains how to verify your current setup and data against the capabilities of the Planning Optimization functionality. 
author: ChristianRytt
manager: tfehr
ms.date: 04/17/2020
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
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.9

---
# Planning Optimization fit analysis

[!include [banner](../../includes/banner.md)]

To see how compatible your current setup and data are with the Planning Optimization functionality, go to **Master planning** \> **Setup** \> **Planning Optimization fit analysis**, and then select **Run analysis**. If the analysis finds any inconsistencies, they are listed on the same page. (The analysis can take a few minutes to run.)

> [!NOTE]
> If inconsistencies are found, you can still use Planning Optimization. The results of the fit analysis just show places where the planning service won't honor your current setup. In other words, they show places where some processes might be ignored or might not be supported.

## Analysis results: Example 1

- **Feature:** Production
- **Issue:** Items with a bill of materials (BOM) level greater than zero: 56
- **Explanation:** The fit analysis found 56 items that have a BOM setup for production. Because the current version of Planning Optimization doesn't support production, Planning Optimization will generate planned purchase orders instead of planned production orders. It will also show a warning that lists the affected items.

## Analysis results: Example 2

- **Feature:** Actions
- **Issue:** Coverage groups with actions calculation enabled: 6
- **Explanation:** The fit analysis found six coverage groups where action calculation is turned on. Because the current version of Planning Optimization doesn't support actions, no actions will be generated during master planning.

## Overview of possible results from the fit analysis

The following table shows the various results that can be shown after a fit analysis. Number signs (_\#_) will be replaced with a number that indicates the number of records that have the listed issue.

| Feature | Listed issue | Explanation |
| --- | --- | --- |
| Actions | Coverage groups with Actions calculation enabled: _\#_ | This feature is pending. Currently, actions aren't generated during master planning when Planning Optimization is enabled, regardless of this setting. The main purpose of actions is to suggest changes to existing orders. |
| Base calendars | Calendars using base calendar: _\#_ | This feature is pending. Currently, the base calendar is ignored when Planning Optimization is enabled. |
| Batch disposition codes | Non-nettable batch disposition masters: _\#_ | This feature is pending. Currently, batch disposition codes are ignored when Planning Optimization is enabled. |
| Capable to promise (CTP) | Default order settings with delivery date control set to CTP: _\#_ | This feature is pending. Currently, CTP is ignored when Planning Optimization is enabled, regardless of this setting. |
| Copy static to dynamic plan | Copy of static to dynamic plan is enabled on the master planning parameters. | Planning Optimization doesn't copy the static plan to the dynamic plan, regardless of this setting. In general, this concept is less relevant because of the speed and complete regeneration that Planning Optimization provides. If two or more plans are used, master planning should be triggered for each plan. |
| Firming | Coverage groups with auto firming time fence set: _\#_ | In version 10.0.7 and later, firming is supported as a separate firming batch job after master planning is completed (provided the _Auto-firming for Planning Optimization_ feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Note that auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. |
| Firming | Item coverage records with auto firming set: _\#_ | In version 10.0.7 and later, auto firming is supported as a separate firming batch job after master planning is completed (provided the _Auto-firming for Planning Optimization_ feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Note that auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. |
| Firming | Master plans with auto firming set: _\#_ | In version 10.0.7 and later, auto firming is supported as a separate firming batch job after master planning is completed (provided the _Auto-firming for Planning Optimization_ feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Note that auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. |
| FitAnalysisPlanningItems | Planning Items: _\#_ | This feature is pending. Currently, planning items are handled like regular items when Planning Optimization is enabled. |
| Forecast | Coverage groups with "Include intercompany orders" enabled: _\#_ | This feature is pending. Currently, master planning doesn't include downstream planned demand when Planning Optimization is enabled, regardless of this setting. Note that released/firmed orders still work with the regular intercompany functionality and will cover most scenarios. |
| Forecast | Coverage groups with "Reduce forecast by" setting set to a value different than "Orders": _\#_ | By default, Planning Optimization uses "Reduce forecast by" for orders, regardless of this setting. |
| Forecast | Forecast models with sub models: _\#_ | This feature is pending. Currently, forecasts that use sub-models aren't supported when Planning Optimization is enabled. They will be ignored, regardless of this setting. |
| Forecast | Master plans with "Include supply forecast" enabled: _\#_ | This feature is pending. Currently, supply forecasts aren't supported when Planning Optimization is enabled. They will be ignored, regardless of this setting. |
| Freeze time fence | Coverage groups with freeze time fence set: _\#_ | The freeze time fence isn't often used, and there are currently no plans to include it for Planning Optimization. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. |
| Freeze time fence | Item coverage records with freeze time fence set: _\#_ | The freeze time fence isn't often used, and there are currently no plans to include it for Planning Optimization. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. |
| Freeze time fence | Master plans with freeze time fence set: _\#_ | The freeze time fence isn't often used, and there are currently no plans to include it for Planning Optimization. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. |
| Intercompany | Master plans including planned downstream demand: _\#_ | This feature is pending. Currently, master planning doesn't include downstream planned demand when Planning Optimization is enabled, regardless of this setting. Note that released/firmed orders still work with the normal intercompany functionality and will cover most scenarios. |
| Kanban | Item coverage records with planned order type kanban: _\#_ | This feature is pending. Currently, item coverage that is set to kanban will be ignored when Planning Optimization is enabled. The kanban planned order type will create a warning during master planning, and planned purchase orders will be created to cover the related demand. |
| Kanban | Items with default order type kanban: _\#_ | Currently, a default order type that is set to kanban will be ignored when Planning Optimization is enabled. The kanban default order type will create a warning during master planning, and planned purchase orders will be created to cover the related demand. |
| Production | BOM lines with rounding or multiple setup: _\#_ | This feature is pending. Currently, rounding and multiple setups are ignored on BOM lines when Planning Optimization is enabled, regardless of this setting. |
| Production | BOM/formula lines with formula measurement: _\#_ | This feature is pending. Currently, formula measurement is ignored on BOM and formula lines when Planning Optimization is enabled, regardless of this setting. |
| Production | BOM/formula lines with item substitution (plan groups): _\#_ | This feature is pending. Currently, item substitution (plan groups) is ignored on BOM and formula lines when Planning Optimization is enabled, regardless of this setting. |
| Production | BOM/formula lines with negative quantity: _\#_ | This feature is pending. BOM and formula lines that have negative quantity will be included with a quantity of 0 (zero) and a warning will be issued when Planning Optimization is enabled. |
| Production | BOM/formula lines with resource consumption: _\#_ | This feature is pending. Currently, BOM and formula lines that have resource consumption are ignored when Planning Optimization is enabled. |
| Production | BOM/formula lines with step consumption: _\#_ | This feature is pending. Currently, step consumption is ignored on BOM and formula lines when Planning Optimization is enabled. |
| Production | BOMs with constant scrap or variable scrap defined: _\#_ | This feature is pending. Currently, constant scrap and variable scrap that are defined on BOMs are ignored when Planning Optimization is enabled. |
| Production | BOMs with subcontracting: _\#_ | This feature is pending. Currently, the subcontracting setup on BOMs is ignored when Planning Optimization is enabled, regardless of this setting. |
| Production | BOMs without a site: _\#_ | This feature is pending. Currently, BOMs without a site are ignored when Planning Optimization is enabled. |
| Production | Demand with specific BOM or route requirements defined: _\#_ | This feature is pending. Currently, the specific BOM or route requirements that are defined on the demand (such as a sub-BOM or sub-route on a sales order) are ignored when Planning Optimization is enabled. The standard BOM or route will be used, regardless of this setting. |
| Production | Formula versions with Co/By products: _\#_ | This feature is pending. Currently, co-products and by-products that are associated with the formula version are ignored when Planning Optimization is enabled. |
| Production | Formula versions with Yield: _\#_ | This feature is pending. Currently, yield that is associated with the formula version is ignored when Planning Optimization is enabled. |
| Production | Plans including sequencing: _\#_ | This feature is pending. Currently, sequencing is ignored when Planning Optimization is enabled, regardless of this setting. |
| Production | Released production orders that are not started, where scheduled start is earlier than today: _\#_ | This feature is pending. |
| Production | Resources scheduled with finite capacity: _\#_ | This feature is pending. Currently, resources that are scheduled with finite capacity are ignored when Planning Optimization is enabled. Scheduling is done based on the default lead time from the product. |
| Production | Routes used in planning: _\#_ | This feature is pending. Currently, routes are ignored when Planning Optimization is enabled. The default lead time from the product is used. |
| Production | Sales line reservation using explosion: _\#_ | Sales line reservation that uses explosion isn't supported when Planning Optimization is enabled. |
| Production | Scheduling with explosion of production orders: _\#_ | Scheduling that uses explosion of production orders isn't supported when Planning Optimization is enabled. Production orders can be scheduled individually. |
| Request for quotations | Master plans with request for quotations enabled: _\#_ | This feature is pending. Currently, requests for quotation (RFQs) aren't considered as demand when Planning Optimization is enabled. They will be ignored, regardless of this setting. |
| Requisitions | Master plans with requisitions enabled: _\#_ | This feature is pending. Currently, requisitions aren't considered when Planning Optimization is enabled. They will be ignored, regardless of this setting. |
| Safety margins | Coverage groups with safety margin: _\#_ | This feature is pending. Currently, safety margin is ignored when Planning Optimization is enabled. To compensate for this behavior, you can increase the lead time so that it includes the safety margin. |
| Safety margins | Master plans with safety margin: _\#_ | This feature is pending. Currently, safety margin is ignored when Planning Optimization is enabled, regardless of this setting. To compensate for this behavior, you can increase the lead time so that it includes the safety margin. |
| Safety stock fulfillment | Item coverage records with "Fulfill minimum" different from "Today's date + procurement time": _\#_ | Planning Optimization always uses *Today's date + procurement time*. This change is made to prepare for a simplified planning setup in the future, and to provide an actionable result. If the procurement time isn't included for safety stock, planned orders that are created for current low on-hand inventory will always be delayed because of the lead time. This behavior can cause significant noise and unwanted planned orders. The best practice is to change the setting so that *Today's date + procurement time* is used. |
| Sales quotations | Master plans with sales quotations enabled: _\#_ | This feature is pending. Currently, quotations aren't considered when Planning Optimization is enabled. They will be ignored, regardless of this setting. |
| Shelf life | Master plans with shelf life enabled: _\#_ | This feature is pending. Currently, shelf life isn't considered when Planning Optimization is enabled, regardless of this setting. |

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)
