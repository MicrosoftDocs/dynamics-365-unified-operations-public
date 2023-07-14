---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.31 (February 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.31 preview release.
author: kfend
ms.date: 11/18/2022
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
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30

---

# What's new or changed in Dynamics 365 Finance 10.0.31 (February 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.31. This version has a build number of 10.0.1406 and is available on the following schedule:

- **Preview of release:** October 2022
- **General availability of release (self-update):** January 2023
- **General availability of release (auto-update):** February 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Tax Calculation | Update tax exempt number from customer address | This feature automatically updates the **Tax exempt number** field on the sales order and free text invoice header, based on the customer address that is selected. You can enable this feature by using the **Update tax exempt number from customer address** parameter on the **Tax Calculation parameters** page when the Tax Calculation service is enabled. | Parameter |
| General ledger | Automate ledger settlements process | The automation of ledger settlement uses the Process automation framework to define matching rules and the schedule that they will be run on. You can define matching criteria such as the posting type and financial dimensions. | Feature management |
| Additional languages available | Four additional languages are available | Four new languages are available for user selection in the preferred language list: Korean, Portuguese (Portugal), Vietnamese, and Chinese (Traditional). To select this option, go to **User options \> Preferences \> Language and country/region preference**. | Localized preferences |
|General ledger|	Optimize year-end close|	This feature accelerates the year-end close run by executing the year-end close processing on microservice, illustrates year-end close results, and manages financial dimensions transfer of balance sheet accounts.|	Feature management |
|General ledger|	Financial Dimension Service |	This feature improves performance when you use the Data management framework to import a journal that has a large number of lines. It uses a new micro-service that runs in parallel to the data import. It runs only on the main account and financial dimension data in the journal, and it generates the dimension combinations that are specified in the ledger account string field on the journal lines. The processing converts this string into the structured data storage that the Financial dimension framework uses throughout the rest of the product for validation, summary reporting, and inquiries.|	LCS & Parameter |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Subscription billing | Quotation report | This feature enables a quotation document to be generated from a billing schedule. |
| Subscription billing | Trade agreement integration | Billing schedules can now take advantage of more functionality that is available for trade agreements. Billing schedule lines can be updated with new amounts when the trade agreement is posted or at renewal. Trade agreements that become effective in the middle of a billing period can be weighted with the effective price for the number of days in the billing period. Date consideration is added for tier pricing. When automatic renewal is used, the trade agreement's effective price and billing period dates are compared to retrieve the correct pricing. |
| Subscription billing | Renew automatically for Unbilled revenue billing schedule lines | Billing schedules where lines are marked for unbilled revenue can now be marked for automatic renewal. |
| Subscription billing | Renew automatically for Milestone billing schedule lines | Billing schedules where lines have an item type of **Milestone** can now be marked for automatic renewal. |
| General ledger | Ledger settlement inquiry | A new ledger settlement inquiry lets you view settled, unsettled, or settled and unsettled ledger transactions for a date range and individual main account. The inquiry resembles the trial balance inquiry and requires a date range within a single fiscal year. The inquiry will show the age of unsettled transactions or the settlement ID of settled transactions. |
| General ledger | Account structure activation performance enhancement | This feature allows you to update multiple transaction groups faster by running them simultaneously during account structure changes. You can track your activation status by selecting **View activation status** for detailed results. |
| General ledger | Accounting source explorer advanced filtering | This feature allows you to use advanced filtering on the accounting source explorer page. The filtering options are similar to the filtering available on the existing **Voucher inquiry** page. |
| General ledger | Enhanced performance for source document accounting framework | This feature provides performance improvements to batch postings of source documents so they run more efficiently. This feature initially only affects free text invoice batch posting with more source documents to be supported in future releases. When this feature is enabled, batch posting is split into smaller units of work which prevents system degradation and lessens the chance of issues due to database disconnections. |
| Tax Calculation | Wildcard support in the tax group and item tax group configuration to the Tax Calculation service | The asterisk (\*) wildcard character is now supported by the tax group and item tax group configuration table in Tax Calculation service. Users can enter **\*** to represent all tax codes and **SP\*** to represent tax codes that start with "SP." |
| Tax Calculation | Extended tax calculation data model | <p>The following fields are extended for the Tax Calculation data model:</p><ul><li>Vendor group</li><li>Vendor invoice group</li><li>Customer group</li><li>Customer invoice group</li><li>Order type</li><li>Item group</li></ul> | 

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.31 includes platform updates. To learn more, see [Platform updates for version 10.0.31 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-31.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=758525).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
