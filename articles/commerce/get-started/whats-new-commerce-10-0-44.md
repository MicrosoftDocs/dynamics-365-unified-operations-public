---
title: Preview features in Dynamics 365 Commerce 10.0.44 (April 2025)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.44. 
author: johnmichalak
ms.date: 04/25/2025
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.44

---

# What's new or changed in Dynamics 365 Commerce 10.0.44 (April 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.44. This version has a build number of 10.0.2263.11 and is available on the following schedule:

- **Preview of release:** April 2025
- **General availability of release (self-update):** June 2025
- **General availability of release (auto-update):** July 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Point of Sale | Loyalty upsell prompt | The loyalty upsell prompt feature is designed to prompt store associates to inform customers about their loyalty program status and tier qualifying points. This feature aims to enhance customer engagement and satisfaction, resulting in increased loyalty, repeat purchases, and overall sales. To enable this feature in Commerce headquarters, go to the feature management workspace and enable **Retail Loyalty Upsell Prompt**.  | Admins |
| Payments | Optimized payment flow now available for loyalty payments  |  Like other payment methods, the loyalty payment method now supports the optimized and unified payment user interface (UI). Additional capabilities have been added such as the ability to initiate customer search and view all loyalty cards associated with the customer. This functionality helps cashiers easily find the required information to complete the transaction. | Admins  |
| Point of Sale | Healthcheck view for offline readiness | This feature performs various checks to verify the status and readiness of the offline database, ensuring a smooth switching experience by creating awareness of any issues. This feature is enabled by default. | Admins |
| Point of Sale | Enable toast notifications for data sync failures and unsuccessful offline installation | The additional toast notifications provide more granular visibility to issues that may be preventing offline switch such as data sync failures and unsuccessful offline installations during the app upgrades | Admins |
| Point of Sale | Toast notifications extensibility | This release also features the API availability for extending toast notifications and provides the schema and samples for the same. | Admins |

## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.44 includes platform updates. To learn more, see [Platform updates for version 10.0.44 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-44.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.44, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1026442).

### Dynamics 365 and industry clouds: 2024 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
