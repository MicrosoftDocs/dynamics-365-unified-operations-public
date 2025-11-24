---
title: Preview features in Dynamics 365 Commerce 10.0.45 (September 2025)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.45. 
author: johnmichalak
ms.date: 11/24/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
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
| Point of sale  | Store Commerce offline in iOS and Android public preview  | This release introduces offline capabilities for Store Commerce on iOS and Android devices. You can now use Store Commerce on these platforms even when offline, ensuring seamless operations and reliable business continuity. Key features include support for SQLite-based offline capabilities, a new SDK experience for iOS that enables extensibility in the app and database, database upgrade support, and an enhanced offline registration form. |  Admins |
| Point of sale  | Funds available in external gift cards post-payment  | By default, the balance on gift cards is added immediately when a cashier issues a gift card or adds funds to it. This action happens before the customer completes payment, which increases the business risk until the customer completes the payment. In Commerce version 10.0.45, Microsoft introduces a feature that delays the balance addition until after payment is successfully received, which reduces operational risk and improves reliability. Learn more in [External gift cards](../dev-itpro/gift-card.md).  |  Admins |
| Point of sale  | Replace Bing Maps with Azure Maps | This feature replaces the deprecated Bing Maps integration with Azure Maps in the Commerce Store app. It ensures continued support for map-based functionality and enhances the user experience with improved performance, security, and scalability. Key capabilities include store locator, map rendering, geocoding, and user location detection. | Admins     |
| E-commerce | Azure Maps support in Commerce | With the retirement of the Bing Maps Free and Basic license in 2025, Commerce now supports Azure Maps with this release. Azure Maps can be used to power key location-based experiences including store selector, buy online pick up in store (BOPIS), and address lookup for shipping or delivery. Microsoft continues to support Bing Maps under the Enterprise license on Commerce until 2028. Learn more in [Azure Maps module](../azure-maps-module.md). | Admins |
| E-commerce  | Canonical URL redirection for category and product pages | In Commerce version 10.0.45, Microsoft introduces support for automatic redirection to canonical URLs for category and product detail pages. This enhancement ensures that users and search engines consistently access clean, SEO-friendly URLs—eliminating unnecessary segments or "garbage" values that may appear between the domain and the product/category ID. Learn more in [Redirect category and product pages to canonical URLs](../e-commerce-extensibility/add-custom-redirect.md). | Admins     |
| E-commerce  | Typescript update  | Typescript is upgraded from 3.9.7 to 4.2.4 to make the Commerce platform more scalable, reliable, and maintainable.|  |
| E-commerce  | Anonymous checkout | To allow anonymous checkouts on an e-commerce site, you must enable the **Allow anonymous checkout** configuration on the online functionality profile associated with the online channel, and also enable anonymous checkout in Commerce site builder.| Admins |
| Unified pricing management | Enable custom price attributes for POS and e-commerce | The unified pricing feature provides a simplified approach for defining custom attributes for customers and products in Dynamics 365 Commerce headquarters. You can easily implement these custom attributes with minimal customization using the Commerce Scale Unit (CSU), enabling pricing flexibility in POS and e-commerce store operations. | Admins     |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.43. You can still disable these features in the **Feature management** workspace, if necessary.

| Module | Feature name | More information |
|--|--|--|
| Retail and commerce | Validate mode of delivery on retail channel sales quotation | This feature ensures that only valid modes of delivery are used with e-commerce sales quotations. |
| Retail and commerce | Enable generation of a stronger channel reference ID | This feature generates a more secure 12-character channel reference ID (also known as an order confirmation ID) that's passed in the query string when an order is looked up. |

## Resources

### Platform updates for finance and operations apps

Dynamics 365 Commerce version 10.0.45 includes platform updates. Learn more in [Platform updates for version 10.0.45 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-45.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.45, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1043223).

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). This plan captures all the details, end to end, top to bottom, in a single document you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md). This notice is usually posted 12 months before a feature is removed.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
