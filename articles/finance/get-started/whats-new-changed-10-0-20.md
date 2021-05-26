---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.20 (July 2021)
description: This topic describes features that are either new or changed in the Dynamics 365 Finance version 10.0.19 preview release.
author: roschlom
ms.date: 05/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2021-04-23 
ms.dyn365.ops.version: 10.0.20

---
# Preview features in Dynamics 365 Finance 10.0.20 (July 2021)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.19. This version has a build number of 10.0.837 and is available as follows:

- **Preview release:** April 2021
- **General availability (self-update):** June 2021
- **General availability (auto-update):** July 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365/release-plans/) for official release dates for each feature.

- [Vendor collaboration bank changes](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/vendor-collaboration-bank-changes)

| Feature area | Feature | More information |
|---|---|---|
| Area| Release plan link | Description |
| Area| Release plan link  | Description |

## Feature enhancements included in this release

The following table lists the feature enhancements included in this release. Each of these provides an incremental improvement to an existing feature. Because they are only enhancements, they are not listed on the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted). If you want to use any of these features, you must explicitly enable them in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area | Feature&nbsp;name&nbsp;in feature&nbsp;management | More information |
|---|---|---|
| Cost management | Enable user-defined batch number setup for inventory closing reverse|Inventory closing reverse create batch jobs for each impacted items which might throttle the batch server if there are too many items. This feature enable the process to use the 'Extra batch helpers' which is currently used by inventory closing process. Please can adjust the setting to optimize the performance considering your environment. |
| General ledger | Enhanced filtering on the cash position inquiry | This feature enhances financial dimension filtering on the Cash position inquiry. When enabled, only records that match all entered segment criteria will be returned on the inquiry. Otherwise records that match any entered segment criteria will be returned.  |
| Accounts receivable | @TaxGST:DynamicQRCodeFeature_INName | &nbsp; |
| Area | Name | Description |

## Globalization changes

- [Tax service – supporting multiple VAT ID (preview)](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/tax-service--supporting-multiple-vat-id-preview)
- [Tax service – supporting tax in transfer order (preview)](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/tax-service--supporting-tax-transfer-order-preview)
- [Tax service (preview)](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/tax-service-preview)
- [Electronic Invoicing – configurable Austrian electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-austrian-electronic-invoice)
- [Electronic Invoicing – configurable Belgian electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-belgian-electronic-invoice)
- [Electronic Invoicing – configurable Danish electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-danish-electronic-invoice)
- [Electronic Invoicing – configurable Dutch electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-dutch-electronic-invoice)
- [Electronic Invoicing – configurable Estonian electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-estonian-electronic-invoice)
- [Electronic Invoicing – configurable French electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-french-electronic-invoice)
- [Electronic Invoicing – configurable German electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-german-electronic-invoice)
- [Electronic Invoicing – configurable Norwegian electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-norwegian-electronic-invoice)
- [Electronic Invoicing – configurable Spanish electronic invoice](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-configurable-spanish-electronic-invoice)

## Additional resources

### Platform updates for Finance and Operations apps
Dynamics 365 Finance 10.0.19 includes platform updates. To learn more, see [Platform updates for version 10.0.19 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-19.md). 

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=575415&dbType=3&qc=762ace311d670d27275cb0b6e11d811e4222643ffccdc5681a42a580780b8337).

### Regulatory updates
For information about regulatory updates for Finance and Operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release. 

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
