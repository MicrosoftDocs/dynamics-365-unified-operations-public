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
ms.search.region: Global
ms.custom: bap-template
---

# Planning Optimization fit analysis

[!include [banner](../../includes/banner.md)]

Planning Optimization fit analysis helps you identify where the result might differ between the deprecated master planning engine and Planning Optimization. The system runs this analysis based on your current setup and data.

You should analyze the result from the Planning Optimization fit analysis as part of the migration process. Note that the scope of Planning Optimization isn't equal to the deprecated master planning engine functionality. We recommend that you work with your partner and read the documentation to prepare for the migration.

> [!NOTE]
>
> - Some inconsistencies can't be identified by the Planning Optimization fit analysis. For more information, see [Differences between classic master planning and Planning Optimization](planning-optimization-differences-with-built-in.md).
> - If inconsistencies are found, you can still use Planning Optimization. The results of the fit analysis just show places where the planning service won't honor your current setup. In other words, they show places where some processes might be ignored or might not be supported.

## Run Planning Optimization fit analysis

To run the Planning Optimization fit analysis and view the results, follow these steps.

1. Select a company (legal entity) from the company picker in the navigation bar.
1. Go to **Master planning** \> **Setup** \> **Planning Optimization fit analysis**.
1. On the Action Pane, select **Run analysis**.
1. The system runs the analysis and then shows the results. For each result that's shown, consult the table later in this article to see whether that feature is currently supported for Planning Optimization and, if it isn't yet supported, when support is expected to become available. If no issues exist for your selected company, the result list will be blank, and you'll receive a "No issues found" message.
1. Repeat this procedure for each company in your organization.

## Possible results from the fit analysis

The following table shows the various results that can be shown after a fit analysis. Number signs (*\#*) will be replaced with a number that indicates the number of records that have the listed issue.

> [!IMPORTANT]
> For features that are not yet supported, the following table provides expected availability information that is estimated based on our current roadmap. These estimates are subject to change without notice.

| Feature | Listed issue | Explanation | Expected availability |
| --- | --- | --- | --- |
| Actions | Coverage groups with Actions calculation enabled: *\#* | This feature is now supported. | Supported |
| Base calendars | Calendars using base calendar: *\#* | This feature is now supported. | Supported |
| Batch disposition codes | Non-nettable batch disposition masters: *\#* | This feature is now supported. For more information, see [Use batch disposition codes to mark batches as available or unavailable](../../inventory/batch-disposition-codes.md) | Supported |
| Capable to promise (CTP) | Default order settings with delivery date control set to CTP: *\#* | In Supply Chain Management 10.0.28 and newer, a process called *CTP for Planning Optimization* makes confirmed ship and receipt dates available after the dynamic plan has been run. For older versions of Supply Chain Management, the legacy CTP setting is ignored when Planning Optimization is enabled. | Supported |
| Firming | Coverage groups with auto firming time fence set: *\#* | In version 10.0.7 and later, firming is supported as a separate firming batch job after master planning is completed (provided the *Auto-firming for Planning Optimization* feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. | Supported |
| Firming | Item coverage records with auto firming set: *\#* | In version 10.0.7 and later, auto firming is supported as a separate firming batch job after master planning is completed (provided the *Auto-firming for Planning Optimization* feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. | Supported |
| Firming | Master plans with auto firming set: *\#* | In version 10.0.7 and later, auto firming is supported as a separate firming batch job after master planning is completed (provided the *Auto-firming for Planning Optimization* feature has been enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)). Auto firming for Planning Optimization is based on the order date (start date), not the requirement date (end date). This behavior ensures that firming of planned orders occurs in due time, without having to include lead time in the firming time fence. | Supported |
| Planning items | Planning Items: *\#* | This feature is pending. Currently, planning items are handled like regular items when Planning Optimization is enabled. | 2023 release wave 1 |
| Forecast | Coverage groups with "Include intercompany orders" disabled: *\#* | This feature is now supported. For more information, see [Intercompany planning](Intercompany-planning.md) | Supported |
| Forecast | Coverage groups with "Reduce forecast by" setting set to a value different than "Orders": *\#* | This feature is now supported. For more information, see [Master planning with demand forecasts](demand-forecast.md) | Supported |
| Forecast | Forecast models with sub models: *\#* |  This feature is now supported. For more information, see [Master planning with demand forecasts](demand-forecast.md) | Supported |
| Forecast | Master plans with "Include supply forecast" enabled: *\#* | This feature is now supported, see [Master planning with supply forecasts](supply-forecast.md) | Supported |
| Freeze time fence | Coverage groups with freeze time fence set: *\#* | This feature is pending. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. | 2023 release wave 1 |
| Freeze time fence | Item coverage records with freeze time fence set: *\#* | This feature is pending. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. | 2023 release wave 1 |
| Freeze time fence | Master plans with freeze time fence set: *\#* | This feature is pending. Currently, the freeze time fence setup is ignored when Planning Optimization is enabled, regardless of this setting. | 2023 release wave 1 |
| Intercompany | Master plans including planned downstream demand: *\#* | This feature is now supported. For more information, see [Intercompany planning](Intercompany-planning.md) | Supported |
| Kanban | Item coverage records with planned order type kanban: *\#* | This feature is pending. Currently, item coverage that is set to kanban will be ignored when Planning Optimization is enabled. The kanban planned order type will create a warning during master planning, and planned purchase orders will be created to cover the related demand. | 2024 |
| Kanban | Items with default order type kanban: *\#* | Currently, a default order type that is set to kanban will be ignored when Planning Optimization is enabled. The kanban default order type will create a warning during master planning, and planned purchase orders will be created to cover the related demand. | 2024 |
| Product lifecycle state | Product lifecycle states not active for planning: *\#* | This feature is now supported. For more information, see [Exclude products that have specific product lifecycle states](product-lifecycle-state.md) | Supported |
| Production | BOM lines with rounding or multiple setup: *\#* | This feature is supported as of June 1, 2023. No feature management is required. | Supported|
| Production | BOM/formula lines with formula measurement: *\#* | This feature is supported in version 10.0.33 and higher. To use it, turn on the *Process manufacturing support for Planning Optimization* feature in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). | Supported |
| Production | BOM/formula lines with item substitution (plan groups): *\#* | This feature is pending. Currently, item substitution (plan groups) is ignored on BOM and formula lines when Planning Optimization is enabled, regardless of this setting. | 2023 release wave 1 |
| Production | BOM/formula lines with negative quantity: *\#* | This feature is supported as of June 1, 2023. No feature management is required. | Supported |
| Production | BOM/formula lines with resource consumption: *\#* | This feature is now supported. | Supported|
| Production | BOM/formula lines with step consumption: *\#* | This feature is pending. Currently, step consumption is ignored on BOM and formula lines when Planning Optimization is enabled. | Future wave |
| Production | BOMs with constant scrap or variable scrap defined: *\#* | This feature is now supported. | Supported |
| Production | BOMs with subcontracting: *\#* | This feature is now supported. | Supported |
| Production | BOMs without a site: *\#* | This feature is now supported. For more information, see [Production planning](production-planning.md) | Supported |
| Production | Demand with specific BOM or route requirements defined: *\#* | This feature is now supported. | Supported |
| Production | Formula versions with Co/By products: *\#* | This feature is supported in version 10.0.33 and higher. To use it, turn on the *Process manufacturing support for Planning Optimization* feature in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). | Supported |
| Production | Formula versions with yield: *\#* | This feature is supported in version 10.0.33 and higher. To use it, turn on the *Process manufacturing support for Planning Optimization* feature in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). | Supported |
| Production | Plans including sequencing: *\#* | This feature is pending. Currently, sequencing is ignored when Planning Optimization is enabled, regardless of this setting. | 2023 release wave 1 |
| Production | Released production orders that are not started, where scheduled start is earlier than today: *\#* | This feature is now supported. | Supported |
| Production | Resources scheduled with finite capacity: *\#* | This feature is now supported.| Supported |
| Production | Routes used in planning: *\#* | This feature is supported. | Supported |
| Production | Sales line reservation using explosion: *\#* | This scenario isn't yet supported. Sales line reservations aren't automatically made during explosion.  | Future wave |
| Production | Scheduling with explosion of production orders: *\#* | Scheduling that uses explosion of production orders is supported starting in version 10.0.32, with a private preview available for version 10.0.31 (contact Microsoft Support to request access to the private preview feature on version 10.0.31). A Planning Optimization run is performed for the items contained in the production order and its respective components in its BOM. | Supported from 10.0.32 |
| Request for quotations | Master plans with request for quotations enabled: *\#* | This feature is supported, see [Plan based on quotations and RFQs](quotation-planning.md) | Supported |
| Requisitions | Master plans with requisitions enabled: *\#* | This feature is now supported. For more information, see [Purchase requisitions](purchase-requisitions.md) | Supported |
| Safety margins | Coverage groups with safety margin: *\#* | This feature is now supported. For more information, see [Safety margins](safety-margins.md) | Supported |
| Safety margins | Master plans with safety margin: *\#* | This feature is now supported. For more information, see [Safety margins](safety-margins.md) |  Supported |
| Sales quotations | Master plans with sales quotations enabled: *\#* | This feature is now supported, see [Plan based on quotations and RFQs](quotation-planning.md) | Supported |
| Shelf life | Master plans with shelf life enabled: *\#* | This feature is now supported. | Supported |
| Custom inventory dimensions | Tracking dimension groups with one or more custom inventory dimensions: *\#* | Planning Optimization doesn't yet support custom dimensions, so they won't be taken into account during planning. | 2023 release wave 2 |

## Additional resources

- [Master planning system architecture](../master-planning-architecture.md)
- [Get started with master planning](get-started.md)
- [Differences between classic master planning and Planning Optimization](planning-optimization-differences-with-built-in.md)
- [Parameters not used by Planning Optimization](not-used-parameters.md)
- [View plan history and planning logs](plan-history-logs.md)
- [Run planning for a subset of items](plan-filters.md)
- [Cancel a planning job](cancel-planning-job.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
