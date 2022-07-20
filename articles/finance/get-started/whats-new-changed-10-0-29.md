---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.29 (September 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.29 preview release.
author: kfend
ms.date: 07/15/2022
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
ms.search.validFrom: 2022-07-15
ms.dyn365.ops.version: 10.0.29

---

# What's new or changed in Dynamics 365 Finance 10.0.29 (September 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.29. This version has a build number of 10.0.xxxx and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** October 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|----|----|----|----|
|Tax calculation    |Integration with periodical journal    |[Tax Calculation integration with finance and operations apps](../localizations/global-tax-calcuation-service-overview.md)    |Parameter    |
|Globalization    |(Russia) Import addresses from the State Address Register (GAR)    |Starting in 10.0.29, address import is available in a new State Address Register (GAR) format: Import from GAR. For more informatino, see [Import from State Address Register (GAR)](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/rus-russian-address-format-import-from-GAR)    |Feature management    |
|    |    |    |    |


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Tax calculation              | Tax Calculation service             |Customer/vendor tax exempt numbers from document header can be used as tax group applicability conditions to determine matrix output. For more information, see [Multiple VAT registration numbers]([../localizations/global-tax-calcuation-service-overview.md](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-multiple-vat-registration-numbers))                  |
|Tax calculation              |Tax Calculation service              |Loading address on freee text invoice header can be used as ship from address to build applicability rules. For more information, see [Tax calculation data model](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tax-calculation-data-model-overview)                  |
|Tax calculation              |Tax Calculation service              |"Adjust execution sequence" function is available now in applicability rule matrix to support adjusting applicabulity rule execution seuqnce within the same weight. For more information, see [Sales tax applicability and sales tax group determination logic](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/global-sales-tax-group-determination?toc=%2Fdynamics365%2Ffinance%2Ftoc.json#matching-logic)                 |
|Budget Control|Budget control document filtering enhancement|This feature provides a query-based filter option for each document that is included in budget control, so that you can specify which budget control documents are budget checked. This release adds the ability for journals to be filtered by a user defined query extending this feature from the prior release.|
|Budget Control|Budget control data maintenance - journal reprocessing|This enhancement to budget control data maintenance allows for reprocessing of budget data for journal documents|
|General Ledger|Default journal sorting direction|This enhancement to journals allows for selecting the journal list to have the default sorting set to either ascending or descending by journal batch number. The sorting direction is set in the general ledger parameters.|
| | | |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release.

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
