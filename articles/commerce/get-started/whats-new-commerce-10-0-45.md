---
title: Preview features in Dynamics 365 Commerce 10.0.45 (September 2025)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.45. 
author: johnmichalak
ms.date: 07/28/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.45

---

# What's new or changed in Dynamics 365 Commerce 10.0.45 (September 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.45. This version has a build number of 10.0.2345 and is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September 2025
- **General availability of release (auto-update):** October 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Point of sale  | Store Commerce offline in iOS and Android Public Preview  | This release introduces offline capabilities for Store Commerce on iOS and Android devices. You can now use Store Commerce on these platforms even when offline, ensuring seamless operations and reliable business continuity. Key features include support for SQLite-based offline capabilities, a new SDK experience for iOS that enables extensibility in the app and database, database upgrade support, and an enhanced offline registration form. |  admins |
| Point of sale  | Funds available in external gift cards post-payments  | By default, the balance on gift cards is added immediately when a cashier issues a gift card or loads funds onto it—**before** the customer completes payment which increases the business risk until the customer completes the payment. Starting with version **10.0.45**, a new feature is available that **delays the balance addition** until **after payment is successfully received**. Thus, reducing operational risk and improving reliability. Learn more: [External gift cards](../dev-itpro/gift-card.md)  |  admins |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.43. You can still turn these features off in **Feature management**, if necessary.

| Module | Feature name | More information |
|--|--|--|
| Retail and commerce | *Validate Mode of Delivery on Retail Channel Sales Quotation* | This feature ensures that only valid mode of deliveries can be used with commerce sales quotations. |
| Retail and commerce | *Enable generation of a stronger channel reference ID* | This feature generates a more secure 12-character channel reference ID (order confirmation ID) that can be passed in the query string when an order is looked up. |

## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.45 includes platform updates. To learn more, see [Platform updates for version 10.0.45 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-45.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.45, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1043223).

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
