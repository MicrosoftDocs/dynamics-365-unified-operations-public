---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.31 (January 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.31 preview release.
author: kfend
ms.date: 10/06/2022
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

# What's new or changed in Dynamics 365 Finance 10.0.31 (January 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.31. This version has a build number of 10.0.xx and is available on the following schedule:

- **Preview of release:** October 2022
- **General availability of release (self-update):** January 2023
- **General availability of release (auto-update):** February 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Tax Calculation             |Update tax exempt number from customer address         | This feature will automatically update "Tax exempt number" field on sales order and free text invoice header based on the selected customer address. User can turn on this feature using parameter "Update tax exempt number from customer address" from "Tax Calculation Parameters"  when Tax Calculation service is enabled.               | Parameter           |
| General ledger     | Automate ledger settlements process       |  The automation of Ledger settlement uses the Process automation framework to define matching rules, along with the schedule for when the rules will be run. Users can define matching criteria such as Posting type and Financial dimensions.  |  Feature management          |


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Subscription billing  | Quotation report | This feature provides the ability to generate a quotation document from a billing schedule. |
| Subscription billing  | Trade agreement integration | Billing schedules can now leverage more functionality available in Trade agreements. Billing schedule lines can be updated with new amounts at the time the trade agreement is posted or at renewal. Trade agreements that become effective in the middle of a billing period can be weighted with the effective price for the number of days in the billing period. Date consideration is added for tier pricing. When using renew automatically the trade agreement’s effective price and billing period dates are compared to retrieve the proper pricing. |
| Subscription billing  | Renew automatically for Unbilled revenue billing schedule lines | Billing schedules with lines that are marked for Unbilled revenue will now have the ability to be marked to renew automatically. |
| Subscription billing  | Renew automatically for Milestone billing schedule lines | Billing schedules with lines that have an item type of Milestone will now have the ability to be marked to renew automatically. |
| General ledger  | Ledger settlement inquiry | The Ledger settlement inquiry has been added to view settled, unsettled, or settled and unsettled ledger transactions for a date range and individual main account. The inquiry is similar to the trial balance, requiring a date range within a single fiscal year. The inquiry will display the age of unsettled transactions, or the settlement ID for settled transactions.  |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.31 includes platform updates. To learn more, see [Platform updates for version 10.0.31 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-31.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release.

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
