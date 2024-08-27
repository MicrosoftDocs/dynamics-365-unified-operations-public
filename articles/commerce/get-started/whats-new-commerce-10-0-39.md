---
title: Preview features in Dynamics 365 Commerce 10.0.39 (April 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.39. 
author: v-chgri
ms.date: 08/27/2024
ms.topic: whats-new
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.custom: 
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Commerce 10.0.39 (April 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.39. This version has a build number of 10.0.1860.32 and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** March 2024
- **General availability of release (auto-update):** April 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Point of sale (POS) | Exclude orders from aggregation - Poland | Poland fiscal regulations mandate that customers must be provided with a printed invoice upon request for up to four weeks following a transaction under certain conditions. However, order aggregation prevents those orders from being retrieved in Commerce headquarters. This feature excludes qualifying orders from being aggregated so that they're available to be opened individually in headquarters. | IT administrators |
| Point of sale (POS)| Customer insights by Copilot^ | Enhance customer interactions and create personalized shopping experiences with Copilot, empowering store associates through data-driven insights. For more information, see [Customer insights by Copilot](../copilot-pos-customer-insights.md)| IT administrators |
| Point of sale (POS) | Report insights by Copilot^| Enhance efficiency, accuracy, and real-time sales analysis with Copilot’s narrative summaries for store reports in the Store Commerce app. For more information, see [Store report insights by Copilot](../copilot-pos-report-insights.md)| IT administrators |
| Point of sale (POS) | Product insights by Copilot^| Copilot empowers store associates to efficiently share product details and promotions, enhancing cross-selling and customer experience. | IT administrators |
| Commerce headquarters | Statement insights by Copilot*| Copilot’s statement posting summary and insights feature provides actionable insights on failed transactions, helping you prioritize and resolve issues efficiently, saving time and effort for your operations team. For more information, see [Enable Copilot statement posting summaries](../copilot-statement-summaries.md) | IT administrators (Enabled by default) |
| Commerce headquarters | Merchandising insights by Copilot* | Copilot streamlines your retail merchandising by proactively summarizing insights and resolving configuration issues effortlessly. For more information, see [Streamline your merchandising process with Copilot-based insights](../copilot-based-merch-insights.md)| IT administrators |

^ 10.0.39, PQU-4 onwards (CSU : 9.49.24184.3, Store Comm. App 9.49.24193.1)

\* 10.0.39 with PQU-3 onwards


## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.39 includes platform updates. To learn more, see [Platform updates for version 10.0.39 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-39.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.39, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=886261).

### Dynamics 365 and industry clouds: 2023 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
