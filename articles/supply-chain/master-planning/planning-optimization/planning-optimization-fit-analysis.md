---
title: Planning Optimization fit analysis
description: This article explains how to verify your current setup and data against the capabilities of the Planning Optimization functionality. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: MpsFitAnalysis, MpsIntegrationParameters
ms.topic: conceptual
ms.date: 01/30/2023
audience: Application User
ms.custom: bap-template
---

# Planning Optimization fit analysis

[!include [banner](../../includes/banner.md)]

Planning Optimization fit analysis helps you to identify where the result might differ between the deprecated master planning engine and Planning Optimization. The system runs this analysis based on your current setup and data.

You should analyze the result from the Planning Optimization fit analysis as part of the migration process. Note that the scope of Planning Optimization is not equal to the deprecated master planning engine functionality. We recommend that you work with your partner and read the documentation to prepare for the migration.

> [!NOTE]
>
> - Some inconsistencies can't be identified by the Planning Optimization fit analysis. For more information, see [Differences between classic master planning and Planning Optimization](planning-optimization-differences-with-built-in.md).
> - If inconsistencies are found, you can still use Planning Optimization. The results of the fit analysis just show places where the planning service won't honor your current setup. In other words, they show places where some processes might be ignored or might not be supported.

## Run Planning Optimization fit analysis

To run the Planning Optimization fit analysis and view the results, follow these steps:

1. Select a company (legal entity) from the company picking in the navigation bar.
1. Go to **Master planning** \> **Setup** \> **Planning Optimization fit analysis**.
1. On the Action pane, select **Run analysis**.
1. The system runs the analysis and then displays the results. For each result shown, consult the table later in this article to see whether that feature is currently supported for Planning Optimization and, if not, when support is expected to become available. If no issues exist for your selected company, then the result list will be empty and you'll get the message "No issues found".
1. Repeat this procedure for each company in your organization.

## Possible results from the fit analysis

The following table shows the various results that can be shown after a fit analysis. Number signs (*\#*) will be replaced with a number that indicates the number of records that have the listed issue.

> [!IMPORTANT]
> For features that are not yet supported, the following table provides expected availability information that is estimated based on our current roadmap. These estimates are subject to change without notice.

| Feature | Listed issue | Explanation | Expected availability |
| --- | --- | --- | --- |
| Actions | Coverage groups with Actions calculation enabled: *\#* | This feature is now supported. | Supported |
| Base calendars | Calendars using base calendar: *\#* | This feature is now supported. | Supported |
| Batch disposition codes | Non-nettable batch disposition masters: *\#* | This feature is now supported. For additional information, see [Use batch disposition codes to mark batches as available or unavailable](../../inventory/batch-disposition-codes.md) | Supported |
| Capable to promise (CTP) | Default order settings with delivery date control set to CTP: *\#* | In Supply Chain Management 10.0.28 and newer, a process called *CTP for Planning Optimization* makes confirmed ship and receipt dates available after the dynamic plan has been run. For older versions of Supply Chain Management, the legacy CTP setting is ignored when Planning Optimization is enabled. | Supported |
| Firming | Coverage groups with auto firming time fence set: *\#* | In version 10.0.7 and later, firming is supported as a separate firming batch job after master planning is completed (provided the *Auto-firming for Planning Optimization* feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Note that auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. | Supported |
| Firming | Item coverage records with auto firming set: *\#* | In version 10.0.7 and later, auto firming is supported as a separate firming batch job after master planning is completed (provided the *Auto-firming for Planning Optimization* feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Note that auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. | Supported |
| Firming | Master plans with auto firming set: *\#* | In version 10.0.7 and later, auto firming is supported as a separate firming batch job after master planning is completed (provided the *Auto-firming for Planning Optimization* feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Note that auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. | Supported |
| FitAnalysisPlanningItems | Planning Items: *\#* | This feature is pending. Currently, planning items are handled like regular items when Planning Optimization is enabled. | 2022 release wave 2 or later |
| Forecast | Coverage groups with "Include intercompany orders" enabled: *\#* | This feature is now supported. For additional information, see [Intercompany planning](Intercompany-planning.md) | Supported |
| Forecast | Coverage groups with "Reduce forecast by" setting set to a value different than "Orders": *\#* | This feature is now supported. For additional information, see [Master planning with demand forecasts](demand-forecast.md) | Supported |
| Forecast | Forecast models with sub models: *\#* |  This feature is now supported. For additional information, see [Master planning with demand forecasts](demand-forecast.md) | Supported |
| Forecast | Master plans with "Include supply forecast" enabled: *\#* | This feature is now supported, see ,[Master planning with supply forecasts](supply-forecast.md) | Supported |
| Freeze time fence | Coverage groups with freeze time fence set: *\#* | This feature is pending. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. | 2022 release wave 2 |
| Freeze time fence | Item coverage records with freeze time fence set: *\#* | This feature is pending. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. | 2022 release wave 2 |
| Freeze time fence | Master plans with freeze time fence set: *\#* | This feature is pending. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. | 2022 release wave 2 |
| Intercompany | Master plans including planned downstream demand: *\#* | This feature is now supported. For additional information, see [Intercompany planning](Intercompany-planning.md) | Supported |
| Kanban | Item coverage records with planned order type kanban: *\#* | This feature is pending. Currently, item coverage that is set to kanban will be ignored when Planning Optimization is enabled. The kanban planned order type will create a warning during master planning, and planned purchase orders will be created to cover the related demand. | Future wave |
| Kanban | Items with default order type kanban: *\#* | Currently, a default order type that is set to kanban will be ignored when Planning Optimization is enabled. The kanban default order type will create a warning during master planning, and planned purchase orders will be created to cover the related demand. | Future wave |
| Product lifecycle state | Product lifecycle states not active for planning: *\#* | This feature is now supported. For additional information, see [Exclude products that have specific product lifecycle states](product-lifecycle-state.md) | Supported |
| Production | BOM lines with rounding or multiple setup: *\#* | This feature is pending. Currently, rounding and multiple setups are ignored on BOM lines when Planning Optimization is enabled, regardless of this setting. | Future wave|
| Production | BOM/formula lines with formula measurement: *\#* | This feature is pending. Currently, formula measurement is ignored on BOM and formula lines when Planning Optimization is enabled, regardless of this setting. | 2022 release wave 2 |
| Production | BOM/formula lines with item substitution (plan groups): *\#* | This feature is pending. Currently, item substitution (plan groups) is ignored on BOM and formula lines when Planning Optimization is enabled, regardless of this setting. | 2022 release wave 2 |
| Production | BOM/formula lines with negative quantity: *\#* | This feature is pending. BOM and formula lines that have negative quantity will be included with a quantity of 0 (zero) and a warning will be issued when Planning Optimization is enabled. Update master data to avoid warnings. | 2022 release wave 2 |
| Production | BOM/formula lines with resource consumption: *\#* | This feature is pending. Currently, BOM and formula lines that have resource consumption are ignored when Planning Optimization is enabled. When this feature is supported, the material requirement will be set to the production start date. Until this feature is supported, requirements will not be generated for materials that are marked with a resource consumption flag. | 2022 release wave 2 |
| Production | BOM/formula lines with step consumption: *\#* | This feature is pending. Currently, step consumption is ignored on BOM and formula lines when Planning Optimization is enabled. | 2022 release wave 2 |
| Production | BOMs with constant scrap or variable scrap defined: *\#* | This feature is pending. Currently, constant scrap and variable scrap that are defined on BOMs are ignored when Planning Optimization is enabled. | 2022 release wave 2 |
| Production | BOMs with subcontracting: *\#* | This feature is now supported. | Supported |
| Production | BOMs without a site: *\#* | This feature is now supported. For additional information, see [Production planning](production-planning.md) | Supported |
| Production | Demand with specific BOM or route requirements defined: *\#* | This feature is pending. Currently, the specific BOM or route requirements that are defined on the demand (such as a sub-BOM or sub-route on a sales order) are ignored when Planning Optimization is enabled. The standard BOM or route will be used, regardless of this setting. | 2022 release wave 2 |
| Production | Formula versions with Co/By products: *\#* | This feature is pending. Currently, co-products and by-products that are associated with the formula version are ignored when Planning Optimization is enabled. | 2022 release wave 2 |
| Production | Formula versions with Yield: *\#* | This feature is pending. Currently, yield that is associated with the formula version is ignored when Planning Optimization is enabled. | 2022 release wave 2 |
| Production | Plans including sequencing: *\#* | This feature is pending. Currently, sequencing is ignored when Planning Optimization is enabled, regardless of this setting. | 2022 release wave 2 |
| Production | Released production orders that are not started, where scheduled start is earlier than today: *\#* | This feature is pending. Currently, if a production order is delayed, then master planning will assume that it will be completed today. This is relevant for released production orders where a delivery date is in the past, but it has not been completed yet. | 2022 release wave 2 |
| Production | Resources scheduled with finite capacity: *\#* | This feature is now supported.| Supported |
| Production | Routes used in planning: *\#* | This feature is supported. | Supported |
| Production | Sales line reservation using explosion: *\#* | Sales line reservation that uses explosion isn't supported when Planning Optimization is enabled. | 2022 release wave 2 |
| Production | Scheduling with explosion of production orders: *\#* | Scheduling that uses explosion of production orders isn't supported when Planning Optimization is enabled. Production orders can be scheduled individually. | 2022 release wave 2 |
| Request for quotations | Master plans with request for quotations enabled: *\#* | This feature is supported, see [Plan based on quotations and RFQs](quotation-planning.md) | Supported |
| Requisitions | Master plans with requisitions enabled: *\#* | This feature is now supported. For additional information, see [Purchase requisitions](purchase-requisitions.md) | Supported |
| Safety margins | Coverage groups with safety margin: *\#* | This feature is now supported. For additional information, see [Safety margins](safety-margins.md) | Supported |
| Safety margins | Master plans with safety margin: *\#* | This feature is now supported. For additional information, see [Safety margins](safety-margins.md) |  Supported |
| Sales quotations | Master plans with sales quotations enabled: *\#* | This feature is now supported, see [Plan based on quotations and RFQs](quotation-planning.md) | Supported |
| Shelf life | Master plans with shelf life enabled: *\#* | This feature is now supported. | Supported |

## Additional resources

- [Master planning system architecture](../master-planning-architecture.md)
- [Get started with master planning](get-started.md)
- [Differences between classic master planning and Planning Optimization](planning-optimization-differences-with-built-in.md)
- [Parameters not used by Planning Optimization](not-used-parameters.md)
- [View plan history and planning logs](plan-history-logs.md)
- [Run planning for a subset of items](plan-filters.md)
- [Cancel a planning job](cancel-planning-job.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
