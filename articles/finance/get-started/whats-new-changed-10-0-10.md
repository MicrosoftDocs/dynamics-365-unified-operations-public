---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.10 (May 2020)
description: This article describes features that are either new or changed in Dynamics 365 Finance 10.0.10.
author: kfend
ms.date: 04/08/2020
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
ms.search.validFrom: 2020-03-05 
ms.dyn365.ops.version: 10.0.10

---
# What's new or changed in Dynamics 365 Finance 10.0.10 (May 2020)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Finance 10.0.10. This version has a build number of 10.0.420 and is available as follows:

- **Preview release:** March 2020
- **General availability (self-update):** April 2020
- **Auto-update:** May 2020

## Features included in this release
The following features are included in this release. The feature titles link to additional information on the [Release plans](/dynamics365/release-plans/) site. 

- [Budget planning query optimization for performance](/dynamics365-release-plan/2020wave1/dynamics365-finance/budget-planning-query-optimization-performance)

 - [Date range for Posted transactions by journals report](/dynamics365-release-plan/2020wave1/dynamics365-finance/date-range-posted-transactions-journals-report)
 
 - [Add Vendor ID, Customer ID, Vendor Name and Customer Name to the voucher transactions list page](/dynamics365-release-plan/2020wave1/dynamics365-finance/add-vendor-id-customer-id-vendor-name-customer-name-voucher-transactions-list-page)
 
 - [Prohibit submission to workflow when the invoice total and registered invoice total are not equal](/dynamics365-release-plan/2020wave1/dynamics365-finance/prohibit-submission-workflow-when-invoice-total-registered-invoice-total-are-not-equal)
 
 - [Allow Interest distribution and Escheatment to use feature – Lets you update bank balances when posting advanced ledger entries](/dynamics365-release-plan/2020wave1/dynamics365-finance/allow-interest-distribution-escheatment-use-feature--lets-update-bank-balances-when-posting-advanced-ledger-entries)
 
 - [Allow filtering the Tax 1099 detail report by reporting year](/dynamics365-release-plan/2020wave1/dynamics365-finance/allow-filtering-tax-1099-detail-report-reporting-year)

 - [Extended Italian localization: Commission settlement on payments](/dynamics365-release-plan/2020wave1/dynamics365-finance/extended-italian-localization-commission-settlement-payments)
 
 - [Extended Italian localization: Configurable posting profiles for banks and remittance types](/dynamics365-release-plan/2020wave1/dynamics365-finance/extended-italian-localization-configurable-posting-profiles-banks-remittance-types)
 
 - [Extended Italian localization: Protest handling for bills of exchange](/dynamics365-release-plan/2020wave1/dynamics365-finance/extended-italian-localization-protest-handling-bills-exchange)

### Additional enhancements

#### Add vendor ID and vendor name to the Posted projects list page
Enabling this feature will display the Vendor ID and Vendor name on the **Posted projects list page** for any project-related purchase order expenses.

#### Enable default accounting setup for project
This feature will enable the ability to view and edit default accounting setup data. This data includes default financial dimensions and sales tax groups from the project list page, or the project contracts list page. When enabled, there will be a **Show default accounting** menu on the **Project** tab of the **All projects list page**. This menu also displays on the **Project contract** tab of the **Project contracts list page**. Clicking **Show default accounting** will open a FactBox, where you can view and manage specific accounting setup information. This feature lets you complete these actions from the list page, instead of having to open the detail page to complete them.
 
## Additional resources

### Platform updates for finance and operations apps
Dynamics 365 Finance 10.0.10 includes platform updates. To learn more, see [Platform updates for version 10.0.10 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-34.md).

### Bug fixes 
For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=424137&dbType=3&qc=bf63d49dcc96e51eb42ac1dd66c6c5e5d7548f1e176f729e324ea3353b9860cb).

### Regulatory updates
For information about regulatory updates for Dynamics 365 finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release. 

### Dynamics 365: 2020 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2020 release wave 1 plan](/dynamics365-release-plan/2020wave1/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

