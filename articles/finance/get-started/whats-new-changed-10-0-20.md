---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.20 (August 2021)
description: This article describes features that are either new or changed in the Dynamics 365 Finance version 10.0.20 preview release.
author: kfend
ms.date: 07/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2021-05-28 
ms.dyn365.ops.version: 10.0.20

---

# Preview features in Dynamics 365 Finance 10.0.20 (August 2021)

[!include [banner](../includes/banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.20. This version has a build number of 10.0.886 and is available as follows:

- **Preview of release:** May 2021
- **General availability of release (self-update):** July 2021
- **General availability of release (auto-update):** July 2021


## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365/release-plans/) for official release dates for each feature. We may update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information |
|----|----|----|
| Finance insights | [Customer payment predictions](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/customer-payment-predictions) | [Customer payment predictions](../finance-insights/payment-insights-overview.md) |
| Finance insights | [External data for cash flow forecasting](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/external-data-cash-forecasting) | [Use external data in cash flow forecasts](../finance-insights/external-data-in-cash-flow.md) |
| Finance insights | [Forecast bank balance](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/forecast-bank-balance) | [Cash flow forecast](../finance-insights/cash-flow-forecast-intro.md) |
| Finance insights | [Intelligent budget proposal](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/intelligent-budget-proposal) | [Budget proposals](../finance-insights/budget-proposals.md) |
| Finance insights | [Treasurer workspace](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/treasurer-workspace) | [Cash position](../finance-insights/cash-position.md) |

> [!Note]
> The Finance insights add-in must be installed from Lifecycle Services (LCS) before you can turn on Finance insights in the **Feature management** workspace. 

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature&nbsp;name&nbsp;in feature&nbsp;management | More information |
|---|---|---|
| Cost management | Enable user-defined batch number setup for inventory closing reverse|Inventory closing reverse creates batch jobs for each impacted item, which might throttle the batch server if there are too many items. This feature enables the process to use the 'Extra batch helpers', which is currently used by the inventory closing process. You can adjust the setting to optimize the performance considering your environment. |
| General ledger | Enhanced filtering on the cash position inquiry | This feature enhances financial dimension filtering on the cash position inquiry. When enabled, only records that match all entered segment criteria will be returned on the inquiry. Otherwise records that match any entered segment criteria will be returned.  |

## Additional resources

### Platform updates for finance and operations apps
Dynamics 365 Finance 10.0.20 includes platform updates. To learn more, see [Platform updates for version 10.0.20 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-19.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to LCS and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=586707&dbType=3&qc=d0dad8eee2af234e8c288e2a7df14c579004518673d014be511f900cfed008f8).

### Regulatory updates
For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release. 

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

