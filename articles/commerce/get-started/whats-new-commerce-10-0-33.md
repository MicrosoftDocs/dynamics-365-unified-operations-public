---
title: What's new or changed in Dynamics 365 Commerce 10.0.33 (April 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.33. 
author: josaw1
ms.date: 03/03/2023
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-03-31
ms.dyn365.ops.version: 10.0.33
---

# What's new or changed in Dynamics 365 Commerce 10.0.33 (April 2023)

[!include [banner](../includes/banner.md)]


This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.33. This version has a build number of 10.0.1549 and is available on the following schedule:

- **Preview of release:** March 2023
- **General availability of release (self-update):** April 2023
- **General availability of release (auto-update):** May 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
|  Geolocation |  Changes to geolocation targeting. | Commerce now supports resolving external geolocation providers in the first request. This behavior is turned off by default for all external segmentation providers to prevent unpredictable site performance. External provider information isn't resolved on the initial page request, and the default page is shown. To override this default behavior and allow external geolocation providers to show the targeted version of a page on the first request, file a support ticket with [Microsoft Support](https://support.microsoft.com/). | Contact Microsoft.<p><p>For more information, refer to [Device, market, and geolocation targeting](../targeting-overview.md).  |
| Orders |  Create asynchronous customer orders in real time, and fallback to batch process if real time fails.  |  When this feature is enabled in the point of sale (POS) functionality profile, POS will attempt to create a customer order in real time using the Real-time service (RTS). However, the POS screen won't be blocked for the response of the service call. The customer order will be completed with a confirmation number, and if the real time order creation fails, the order will be created in batch after a few minutes.<p><p>[Customer orders in point of sale (POS)](../customer-orders-overview.md) | IT Pro opt-in   |
| Orders  |  Enable on behalf of ordering (OBO).   |  This new functionality allows B2B account managers to sign into the B2B e-commerce website on behalf of the B2B buyers they work with. The account manager can see all the same information that the buyer sees and can take actions such as adding items to the cart and placing orders. The feature requires configuration in Azure Active Directory and site builder.<p><p>[Create and modify B2B pages for on behalf of (OBO) functionality](../obo-add-pages-site-builder.md)<p><p>[Set up and configure on behalf of (OBO) functionality](../obo-configure-hq.md)| IT Pro opt-in |
| POS | Hide and show title bar in Store Commerce app. | The title bar in Store Commerce app for Windows can now be hidden and shown with the Alt-Enter keyboard shortcut. A Windows notification will be displayed when entering or leaving full-screen mode. | Enabled by default |

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Commerce version 10.0.33 includes platform updates. To learn more, see [Platform updates for version 10.0.33 of finance and operations apps (January 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-33.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.33, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=795940).

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.


For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
