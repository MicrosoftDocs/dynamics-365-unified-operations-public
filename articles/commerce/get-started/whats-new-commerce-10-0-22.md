---
# required metadata

title: What's new and changed in Dynamics 365 Commerce 10.0.22 (November 2021)
description: This topic describes features that are either new or changed in the preview release of Dynamics 365 Commerce 10.0.22. 
author: josaw1
ms.date: 09/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2021-09-31 
ms.dyn365.ops.version: 10.0.22

---
# What's new and changed in Dynamics 365 Commerce 10.0.22 (November 2021)

[!include [banner](../includes/banner.md)]


This topic lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.22. This version has a build number of 10.0.995 and is available on the following schedule:

- **Preview of release:** September 2021
- **General availability of release (self-update):** October 2021
- **General availability of release (auto-update):** November 2021


## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature. We may update this topic to include features that made it into the build after this topic was initially published. To determine how to turn on a feature, refer to the **Enabled by** column in the following table. For more information about how to use Feature management, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area   | Feature                                                  | More information                                          |  Enabled by             |
|----------------|----------------------------------------------------------|-----------------------------------------------------------|-------------------------|
|  Customer management | Site builder configuration for product search being inventory aware | [Customer management in stores](../customer-mgmt-stores.md) | Feature management |
|  Customer orders  |  [Enable order lookup for guest checkouts](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/enable-order-lookup-guest-checkouts)    |  [Enable order lookup for guest checkouts](../order-lookup-guest.md)<p>[Order lookup module](../order-lookup-module.md)</p> |  Feature management   |
|  E-commerce      |   [Geo-detection and redirection for e-commerce sites](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/geo-detection-redirection-e-commerce-sites) | [Set up geo detection and redirection](../geo-detection-redirection.md)<p>[Country/region picker module](../country-region-picker-module.md)</p>   |                    Site builder settings    |
| Extensibility | Set up your own local development environment for Dynamics 365 Commerce without Lifecycle Service | [Set up your own local development environment](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.32/src/ScaleUnitSample/.vscode) | |
| Extensibility | Develop Commerce Cloud Scale Unit (CRT and API) extension using Visual Studio Code | [Develop CSU extension using VS Code](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.32/src/ScaleUnitSample/.vscode) | |
| Globalization | (Italy) Lottery code validation | The validation of the lottery code that is specified in a customer master record or for a sales transaction is now based on the format defined for the corresponding registration type. See [Set up a registration type for the lottery code](../localizations/emea-ita-customer-information.md#set-up-a-registration-type-for-the-lottery-code) for more details. | Enabled by default |
| Merchandising | Optimized product availability calculation | [Calculate inventory availability for retail channels](../calculated-inventory-retail-channels.md) | Feature management |
| Merchandising | [Require moderator for ratings and reviews](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/require-moderator-ratings-reviews) | [Enable manual publishing of ratings and reviews by a moderator](../manual-publish-rating-reviews.md) | Site builder settings  |

## Additional resources

### Platform updates for Finance and Operations apps

Dynamics 365 Commerce 10.0.22 includes platform updates. To learn more, see [Platform updates for version 10.0.22 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-22.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=615299).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
