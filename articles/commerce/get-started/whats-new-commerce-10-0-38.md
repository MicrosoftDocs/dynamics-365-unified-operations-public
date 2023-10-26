---
title: Preview features in Dynamics 365 Commerce 10.0.38 (February 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.38. 
author: josaw1
ms.date: 10/27/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.38

---

# What's new or changed in Dynamics 365 Commerce 10.0.38 (February 2024)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]


This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.38. This version has a build number of 10.0.NNNN and is available on the following schedule:

- **Preview of release:** October 2023
- **General availability of release (self-update):** December 2023
- **General availability of release (auto-update):** February 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
|B2B   | Enable site admins to control which business partners can access specific B2B ecommerce websites. | Site admins can now control which business partners have access to specific B2B ecommerce websites. To do so, a site admin must add the online channels of type "B2B" to the customer hierarchy record of the business partner.<p><p>[Manage B2B business partners using customer hierarchies](../b2b/partners-customer-hierarchies.md)| Site admin |
| Copilot | [Generate product enrichment content for e-commerce sites with Copilot in site builder](/dynamics365/release-plan/2023wave2/commerce/dynamics365-commerce/generate-engaging-product-content-e-commerce-websites-using-copilot-dynamics-365-commerce).| Transform your product storytelling and marketing strategy with copilot functionality. This feature allows to you leverage AI-generated product marketing and enrichment content tailored to engage and delight your diverse customer base. | Admin must enable Copilot in site builder through feature configuration available in **Tenant settings**. |
| POS | Cash management for multiple currencies in a store | Cash management operations in the store, such as declare start amount, tender removal, and float entry now support multiple currencies, enabling retailers to manage cash across various currencies in a store. | By default |

## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.38 includes platform updates. To learn more, see [Platform updates for version 10.0.38 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-38.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.38, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](UPDATE).

### Dynamics 365 and industry clouds: 2023 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 2 plan](/dynamics365/release-plan/2023wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.


For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
