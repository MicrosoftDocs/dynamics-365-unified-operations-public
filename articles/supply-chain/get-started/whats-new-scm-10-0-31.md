---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.31 (February 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.31. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 11/07/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.31 (February 2023)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.31. This version has a build number of 10.0.1406 and is available on the following schedule:

- **Preview of release:** October 2022
- **General availability of release (self-update):** January 2023
- **General availability of release (auto-update):** February 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Planning | [Consider sales quotations in Planning Optimization](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/consider-sales-quotations-planning-optimization) | [Plans based on quotations and RFQs](../master-planning/planning-optimization/quotation-planning.md) | Enabled by default |
| Planning | [Leverage supply forecasts in Planning Optimization](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/leverage-supply-forecasts-planning-optimization) | [Master planning with supply forecasts](../master-planning/planning-optimization/supply-forecast.md) | Enabled by default |
| Planning | [Use batch disposition codes in Planning Optimization](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/use-batch-disposition-codes-planning-optimization) | [Use batch disposition codes to mark batches as available or unavailable](../inventory/batch-disposition-codes.md) | Enabled by default |
| Planning | [Use finite material scheduling in Planning Optimization](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/use-finite-material-scheduling-planning-optimization) | [Finite capacity planning and scheduling](../master-planning/planning-optimization/finite-capacity.md) | Feature management:<br>*Finite material scheduling for Planning Optimization.* |
| Procurement | [Assess supply risks to prevent supply chain disruptions](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/assess-supply-risks-prevent-supply-chain-disruptions) | [Supply risk assessment overview](../procurement/supply-risk-assessment-overview.md) | Feature management:<br>*Assess supply risks to prevent supply chain disruptions* |
| Procurement | [Source products and materials from multiple vendors](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/source-products-materials-multiple-vendors) | [Source products and materials from multiple vendors](../master-planning/source-from-multiple-vendors.md) | Feature management:<br>*Source products and materials from multiple vendors using Planning Optimization* |
| Product information management | [Display product info in user's language](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/display-product-info-users-language) | [Show translated product names and descriptions in the UI](../pim/show-translated-product-info.md) | Feature management:<br>*Display product info in user’s language* |
| Warehouse management | [Auto-submit detour steps for the Warehouse Management mobile app](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/auto-submit-detour-steps-warehouse-management-mobile-app) | [Configure detours for steps in mobile device menu items](../warehousing/warehouse-app-detours.md) | Feature management<br>*Auto-submit detour steps for the Warehouse Management mobile app* |
| Warehouse management | [Guided warehouse implementation experience](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/guided-warehouse-implementation-experience) | [Get started with setting up the Warehouse management module](../warehousing/get-started-with-setting-up-module.md)<br><br>[Test location directives with acceptance tests](../warehousing/location-directive-acceptance-tests.md) | Enabled by default |
| Warehouse management | [Optimize warehousing setup with Application Insights](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/optimize-warehousing-setup-application-insights) | [Enable warehousing telemetry with Application Insights](../warehousing/application-insights-warehousing.md)<br><br>[Monitor Warehouse Management usage and performance](../warehousing/application-insights-monitor-usage-performance.md) | Feature management<br>*Operational insights* |
| Warehouse management | [Pack shipments with the Warehouse Management mobile app](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/pack-shipments-warehouse-management-mobile-app) | [Packing containers with the Warehouse Management mobile app](../warehousing/warehouse-app-packing-containers.md)<br><br>[Example scenario – Pack containers with the Warehouse Management mobile app](../warehousing/warehouse-app-pack-containers-scenario.md)<br><br>[Container label layouts and printing](../warehousing/print-container-labels.md) | Feature management<br>*Pack containers using the Warehouse Management mobile app* |
| Additional languages available | Four additional languages are available | Four new languages are available for user selection in the preferred language list: Korean, Portuguese (Portugal), Vietnamese, and Chinese (Traditional). To select this option, go to **User options \> Preferences \> Language and country/region preference**. | Localized preferences |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Master planning | Restart and resume logic for the forecast generation batch process. | This feature enables the forecast generation batch process to be restarted or resumed after an infrastructure failure occurs. |
| Production control | Enable use of a numpad in the sign-in page | This feature lets admins add a numpad control to the sign-in page for production floor execution. Workers can then sign in by using the numpad to enter their badge ID or personal number. |
| Sales and marketing | Settle customer payment deductions using the matching invoice | <p>This feature adds an option that lets you settle customer payment deductions by using the invoice that is selected for each deduction. When you use this option, the system automatically settles deduction transactions by using the matching invoice, if an open balance exists for that invoice. Otherwise, the deduction isn't automatically settled. If you don't use this option, the system settles deduction transactions by using the open amount for payment invoices, as was the standard behavior in Supply Chain Management version 10.0.24 and earlier.</p><p>This feature adds a new **Settle customer payment deductions** field to the **Accounts receivable parameters** page. Set this field to *Match to invoice* to use the new functionality. Set it to *Match to open payments* to use the previous behavior.</p><p>By default, when you first enable this feature, the **Settle customer payment deductions** field is set to *Match to invoice* (that is, the new behavior is used). The *Match to open payments* option is provided mainly to support legacy integration scenarios. |
| Transportation management | Generate data manually on voyage editor | This feature lets you manually generate data for the **Voyage editor** page as it's required. Because data is no longer generated each time that a filter value is changed, this feature helps improve system performance and the user experience. |
| Warehouse management | Location directive scopes | <p>This feature gives you more flexibility when you design location directives, and it helps reduce redundant configurations. It adds a **Scopes** option to the **Location directives** page. This option replaces the previous **Multiple SKU** option. Whereas the **Multiple SKU** option can be set only to *Yes* or *No*, the **Scopes** option provides not only those two settings (through the *Single item* and *Multiple items* values) but also two more (through the *Single item or order* and *All* values).</p><p>For more information, see [Work with location directives](../warehousing/create-location-directive.md).</p> |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Master planning | [Master planning for products with limited shelf life](../master-planning/planning-optimization/shelf-life.md)<br>[Run planning for a subset of items](../master-planning/planning-optimization/plan-filters.md) |
| Warehouse management | [Manually handle sales and transfer line picking exceptions](../warehousing/manual-order-line-picking-exception-handling.md) |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.31 includes platform updates. To learn more, see [Platform updates for version 10.0.31 of Finance and Operations apps (February 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-31.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.31, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=758525).

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
