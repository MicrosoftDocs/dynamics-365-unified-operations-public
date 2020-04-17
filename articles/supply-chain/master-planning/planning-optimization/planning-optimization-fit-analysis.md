---
# required metadata

title: Planning Optimization fit analysis
description: This topic explains how to verify your current setup and data against the capabilities of the Planning Optimization functionality. 
author: ChristianRytt
manager: tfehr
ms.date: 10/30/2019
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
ms.dyn365.ops.version: AX 10.0.5

---
# Planning Optimization fit analysis

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

To see how compatible your current setup and data are with the Planning Optimization functionality, go to **Master planning** \> **Setup** \> **Planning Optimization fit analysis**, and then select **Run analysis**. If the analysis finds any inconsistencies, they are listed on the same page. (The analysis can take a few minutes to run.)

> [!NOTE]
> If inconsistencies are found, you can still use Planning Optimization. The results of the fit analysis just show places where the planning service won't honor your current setup. In other words, they show places where some processes might be ignored or might not be supported.

### Analysis results: Example 1

- **Feature:** Production
- **Issue:** Items with BOM level greater than zero: 56
- **Explanation:** The fit analysis found 56 items that have a bill of materials (BOM) setup for production. Because the current version of Planning Optimization doesn't support production, Planning Optimization will generate planned purchase orders instead of planned production orders. It will also show a warning that lists the affected items.

### Analysis results: Example 2

- **Feature:** Actions
- **Issue:** Coverage groups with actions calculation enabled: 6
- **Explanation:** The fit analysis found six coverage groups where action calculation is turned on. Because the current version of Planning Optimization doesn't support actions, no actions will be generated during master planning.

## Overview of possible results from the Fit Analysis

The following table shows the various results that can be displayed, as result from the fit analysis. The # will be a number that indicate the amount of records with the listed issue. 

| **Feature** | **Listed issue**    | **Explanation** |
| --- | --- | --- |
| Actions | Coverage groups with Actions calculation enabled: # | This is a pending feature. Currently Actions are not being generated during master planning with Planning Optimization, regardless of this setting. The main purpose of actions is to suggest changes to existing orders. |
| Base calendars | Calendars using base calendar: # | This is a pending feature. Currently base calendar is ignored with Planning Optimization enabled. |
| Batch disposition codes | Non-nettable batch disposition masters: # | This is a pending feature. Currently Batch disposition codes are ignored with Planning Optimization enabled. |
| Capable to promise | Default order settings with delivery date control set to CTP: # | This is a pending feature. Currently CTP is ignored with Planning Optimization enabled, regardless of this setting. |
| Copy static to dynamic plan | Copy of static to dynamic plan is enabled on the master planning parameters. | Planning Optimization do not copy the static plan to the dynamic plan, regardless of this setting. In general, this concept is less relevant with the speed and complete regeneration provided with Planning Optimization. If two, or more, plans are used master planning should be triggered for each plan. |
| Firming | Coverage groups with auto firming time fence set: # | Firming is supported with feature management from version 10.0.7, as a separate firming batch job after master planning is completed. Note that Auto firming for Planning Optimization is based on order date (start date), not requirement date (end date). This ensures that firming of planned order happens in due time, without having to include lead time in the firming time fence. |
| Firming | Item coverage records with auto firming set: # | Auto firming is supported with feature management from version 10.0.7, as a separate firming batch job after master planning is completed. Note that Auto firming for Planning Optimization is based on order date (start date), not requirement date (end date). This ensures that firming of planned order happens in due time, without having to include lead time in the firming time fence. |
| Firming   | Master plans with auto firming set: # | Auto firming is supported with feature management from version 10.0.7, as a separate firming batch job after master planning is completed. Note that Auto firming for Planning Optimization is based on order date (start date), not requirement date (end date). This ensures that firming of planned order happens in due time, without having to include lead time in the firming time fence. |
| FitAnalysisPlanningItems | Planning Items: # | This is a pending feature. Currently Planning items will be handled like regular items with  Planning Optimization enabled. |
| Forecast | Coverage groups with &quot;Include intercompany orders&quot; enabled: # | This is a pending feature. Currently master planning do not include downstream planned demand with Planning Optimization enabled, regardless of this setting. Note that released/firmed orders still works with the normal intercompany functionality and cover most scenarios. |
| Forecast | Coverage groups with &quot;Reduce forecast by&quot; setting set to a value different than &quot;Orders&quot;: # | Planning Optimization will default &quot;Reduce forecast by&quot; to Orders, regardless of this setting. |
| Forecast | Forecast models with sub models: # | This is a pending feature. Currently forecast with sub models is not supported with Planning Optimization enabled. They will be ignored regardless of this setting. |
| Forecast | Master plans with &quot;Include supply forecast&quot; enabled: # | This is a pending feature. Currently Supply forecast is not supported with Planning Optimization enabled. Any supply forecast will be ignored, regardless of this setting.   |
| Freeze time fence | Coverage groups with freeze time fence set: # | Usage of freeze time fence have been very limited in the past and is currently not planned for Planning Optimization. Currently freeze time fence is ignored with Planning Optimization enabled, regardless of this setting. |
| Freeze time fence | Item coverage records with freeze time fence set: # | Usage of freeze time fence have been very limited in the past and is currently not planned for Planning Optimization. Currently freeze time fence setup is ignored with Planning Optimization enabled, regardless of this setting. |
| Freeze time fence | Master plans with freeze time fence set: # | Usage of freeze time fence have been very limited in the past and is currently not planned for Planning Optimization. Currently freeze time fence is ignored with Planning Optimization enabled, regardless of this setting. |
| Intercompany | Master plans including planned downstream demand: # | This is a pending feature. Currently master planning does not include downstream planned demand with Planning Optimization enabled, regardless of this setting. Note that released/firmed orders still work with the normal intercompany functionality and cover most scenarios. |
| Kanban | Item coverage records with planned order type kanban: # | This is a pending feature. Currently item coverage set to Kanban will be ignored with Planning Optimization enabled. Planned order type Kanban will create a warning during master planning and planned purchase orders are created to cover the related demand. |
| Kanban | Items with default order type kanban: # | Currently default order type set to Kanban will be ignored with Planning Optimization enabled. Default order type Kanban will create a warning during master planning and planned purchase orders are created to cover the related demand. |
| Production | BOM lines with rounding or multiple setup: # | This is a pending feature. Currently rounding or multiple setup is ignored on BOM lines with Planning Optimization enabled, regardless of this setting.   |
| Production | BOM/formula lines with formula measurement: # | This is a pending feature. Currently formula measurement is ignored on BOM/formula lines with Planning Optimization enabled, regardless of this setting.   |
| Production | BOM/formula lines with item substitution (plan groups): # | This is a pending feature. Currently item substitution (plan groups) is ignored on BOM/formula lines with Planning Optimization enabled, regardless of this setting.  |
| Production | BOM/formula lines with negative quantity: # | This is a pending feature. BOM/formula lines with negative quantity will be included with a quantity of zero and a warning is given with Planning Optimization enabled. |
| Production | BOM/formula lines with resource consumption: # | This is a pending feature. Currently BOM/formula lines with resource consumption are  ignored with Planning Optimization enabled. |
| Production | BOM/formula lines with step consumption: # | This is a pending feature. Currently step consumption is ignored on BOM/formula lines with Planning Optimization enabled.   |
| Production | BOMs with constant scrap or variable scrap defined: # | This is a pending feature. Currently constant scrap or variable scrap defined on BOMs is ignored with Planning Optimization enable d. |
| Production | BOMs with subcontracting: # | This is a pending feature. Currently subcontracting setup on BOMs is ignored with Planning Optimization enabled, regardless of this setup. |
| Production | BOMs without a site: # | This is a pending feature. Currently BOMs without a site is ignored with Planning Optimization enabled.   |
| Production | Demand with specific BOM or route requirements defined: # | This is a pending feature. Currently the speci fic BOM or route requirements defined on the demand (e.g. Sub-BOM or Subroute on a sales order) is ignored with Planning Optimization enabled. Standard BOM or route will be used, regardless of this setup. |
| Production | Formula versions with Co/By products: # | This is a pending feature. Currently Co/By products associated with the formula version are ignored with Planning Optimization enabled.   |
| Production | Formula versions with Yield: # | This is a pending feature. Currently yield associated with the formula version is ignored with Planning Optimization enabled. |
| Production | Plans including sequencing: # | This is a pending feature. Currently Sequencing is ignored with Planning Optimization enabled, regardless of this setting. |
| Production | Released production orders that are not started, where scheduled start is earlier than today: # | This is a pending feature. |
| Production | Resources scheduled with finite capacity: # | This is a pending feature. Currently resources scheduled with finite capacity is ignored with Planning Optimization enabled. Scheduling is done based on default lead time from the product. |
| Production | Routes used in planning: # | This is a pending feature. Currently routes are ignored with Planning Optimization enabled. Lead time is defaulted from the product. |
| Production | Sales line reservation using explosion: # | Sales line reservation using explosion is not supported with Planning Optimization enabled. |
| Production | Scheduling with explosion of production orders: # | Scheduling with explosion of production orders is not supported with Planning Optimization enabled. Production orders can be scheduled individual. |
| Request for quotations | Master plans with request for quotations enabled: # | This is a pending feature. Currently request for quotations are not considered as demand with Planning Optimization enabled and will be ignored, regardless of this setting. |
| Requisitions | Master plans with requisitions enabled: # | This is a pending feature. Currently requisitions are not considered with Planning Optimization enabled and will be ignored, regardless of this setting. |
| Safety margins | Coverage groups with safety margin: # | This is a pending feature. Currently safety margin is ignored with Planning Optimization enabled. To account for this the lead time can be increased to include the desired days of safety margin. |
| Safety margins | Master plans with safety margin: # | This is a pending feature. Currently safety margin is ignored with Planning Optimization enabled, regardless of this setting. To account for this the lead time can be increased to include the safety margin. |
| Safety stock fulfillment | Item coverage records with &quot;Fulfill minimum&quot; different from &quot;Today&#39;s date + procurement time&quot;: # | Planning Optimization always use &#39;Today&#39;s date + procurement time&#39;. This change is done to prepare for a simplified planning setup in the future and to provide an actionable result. Without including the procurement time for safety stock, planned orders created for current low on-hand will always be delayed due to lead time – causing a lot of noise and unwanted planned orders. Best practice is to change the setting to use &#39;Today&#39;s date + procurement time&#39;. |
| Sales quotations | Master plans with sales quotations enabled: # | This is a pending feature. Currently quotes are not considered with Planning Optimization enabled and will be ignored, regardless of this setting. |
| Shelf life | Master plans with shelf life enabled: # | This is a pending feature. Currently shelf life is not considered with Planning Optimization enabled, regardless of this setting. |

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)
