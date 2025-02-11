---
title: Preview features in Dynamics 365 Commerce 10.0.43 (January 2025)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.43. 
author: johnmichalak
ms.date: 02/11/2025
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.40

---

# What's new or changed in Dynamics 365 Commerce 10.0.43 (January 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.43. This version has a build number of 10.0.2177.18 and is available on the following schedule:

- **Preview of release:** January 202
- **General availability of release (self-update):** March 2025
- **General availability of release (auto-update):** April 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Globalization | Enable identical receipt copy printing for France | This feature enables printing an identical duplicate of the original receipt to comply with NF 525 regulatory requirements. When enabled, the receipt copy reproduces all data exactly as it appeared on the original, including details such as the store address at the time of the transaction. | Admins |
| Payments | Minimize fraud in e-commerce transactions by using Adyen's risk management capabilities through the Adyen connector. | Adyen's risk management system empowers customers to effectively detect, mitigate, analyze, and monitor fraud and disputes. Each e-commerce transaction undergoes a thorough risk evaluation process to assess the potential risk associated with the payment. The risk management capabilities must be enabled by Adyen. No additional configuration is needed in Dynamics 365 Commerce. | Admins |
| Point of sale | New network connection health chart  | This feature introduces three new network health charts for connection history, connection types and WIFI signal strength over a 24 hour period. | Admins |
| Point of sale | Proactive toast notifications for offline reliability | This feature supports the toast notification framework in Store Commerce and notifies store employees when there's an offline authentication failure, weak or missing WI-FI, or a seamless offline switch. | Admins |

## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.43 includes platform updates. To learn more, see [Platform updates for version 10.0.43 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-43.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.43, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=985753).

### Dynamics 365 and industry clouds: 2024 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave2/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
