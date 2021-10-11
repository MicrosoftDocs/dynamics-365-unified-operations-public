---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.23 (December 2021)
description: This topic describes features that are either new or changed in the Dynamics 365 Finance version 10.0.23 preview release.
author: kfend
ms.date: 10/08/2021
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
ms.search.validFrom: 2021-10-15 
ms.dyn365.ops.version: 10.0.23

---

# Preview features in Dynamics 365 Finance 10.0.23 (December 2021)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.23. This version has a build number of 10.0.xxx and is available as follows:

- **Preview of release**: October 2021
- **General availability of release (self-update)**: November 2021
- **General availability of release (auto-update)**: December 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365/release-plans/) for official release dates for each feature. We may update this topic to include features that made it into the build after this topic was initially published.

| Feature area | Feature | More information | Enabled by  |
|----|----|----|----|
| Finance insights | [Forecast bank balance](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/forecast-bank-balance) | [Cash flow forecast](../finance-insights/cash-flow-forecast-intro.md) |   |
|Tax Calculation    | [Integration with free text invoice](https://docs.microsoft.com/en-us/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance/tax-calculation-service--integration-free-text-invoice)   | [Tax Calculation integration with Finance and Operation](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tax-calculation-data-model-overview)   | Admins, makers, marketers, or analysts, automatically   |
|    |    |    |    |

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). If you want to use or turn off any of these features, you must do that in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature name in feature management | More information |  
|---|---|---|
| Accounts payable  | Process automation - additional support added for modifying query filters   | This feature lets you add tables and filters to process automation queries that are used when you create or edit series or individual occurrences of the process.  |  
| Tax Calculation  |Tax in transfer order   | This feature is enhanced in 10.0.23 to enable printing tax information on transfer order documents. See [Print tax information on transfer order documents](https://go.microsoft.com/fwlink/?linkid=2174529) for more information.   |  
| Tax Calculation   |Tax Calculation Service   |This feature is enhanced in 10.0.23 to support legal entity's primary address in Japan, Malaysia, Singapore and Thailand. See Supported countries/regions section in [Tax Calculation overview](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/global-tax-calcuation-service-overview?toc=/dynamics365/finance/toc.json#supported-countriesregions) for more information.  |  
| Globalization  | (Russia) Run Inventory balance turnover report calculation in batch  | The feature provides the possibility to run the Inventory balance turnover report in batch, to store the result of the calculation, and to view the reports generated earlier.  |  
|   |   |   |  


## Additional resources

### Platform updates for Finance and Operations apps
Dynamics 365 Finance 10.0.23 includes platform updates. To learn more, see [Platform updates for version 10.0.23 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-23.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=XXXX).

### Regulatory updates
For information about regulatory updates for Finance and Operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release. 

### Dynamics 365: 2021 release wave plans

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 Finance 2021 release wave 2](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
