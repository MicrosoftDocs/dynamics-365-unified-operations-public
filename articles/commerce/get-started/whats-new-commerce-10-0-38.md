---
title: Preview features in Dynamics 365 Commerce 10.0.38 (February 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.38. 
author: josaw1
ms.date: 04/12/2024
ms.topic: article
audience: Application User
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.38

---

# What's new or changed in Dynamics 365 Commerce 10.0.38 (February 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.38. This version has a build number of 10.0.1777 and is available on the following schedule:

- **Preview of release:** October 2023
- **General availability of release (self-update):** December 2023
- **General availability of release (auto-update):** February 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
|  B2B   |  Associate distributors to site and enable selection of distributor from the B2B site.   |  - Bulk channel association: Site builder now includes a feature that allows users to associate multiple channels to their respective sites at the same time. Using the cross-channel functionality, they can author web pages once and make them available by default for all channels associated to the site.<p><p>- Distributor channel search and selection: There is now a distributor channel search and selection tool on B2B sites. B2B Buyers can only view channels that are relevant to them, based on mappings established in Commerce headquarters and site builder.<p><p>- Channel switching with cart integrity: B2B buyers can now quickly switch between distributor channels. For example, when browsing products from one channel, they can switch to another. The cart remains consistent and linked to the original distributor's channel, ensuring that the product selection in one distributor channel's cart doesn't mix with another.<p><p>- Dynamic catalog reset: Upon changing the distributor channel, the product catalog selection is automatically reset, ensuring that users always see products relevant to the chosen distributor channel. | By default  |
|  B2B   | Enable site admins to control which business partners can access specific B2B ecommerce websites. | Site admins can now control which business partners have access to specific B2B ecommerce websites. To do so, a site admin must add the online channels of type "B2B" to the customer hierarchy record of the business partner.<p><p>[Manage B2B business partners using customer hierarchies](../b2b/partners-customer-hierarchies.md)| Site admin |
|  B2B  | Initiate orders on behalf of B2B partners.   |  Customer service personnel using the call center can now initiate orders on behalf of B2B partners (buyers) corresponding to their specific B2B channel. Also, when adding order lines, they can pick items that are solely from B2B catalogs associated with the B2B channel. | Feature management<p><p>"Enable B2B2B setup and enhancements to B2B Commerce orders" |
|   B2B  |  Capture distributor leads as a prospect and provide management access to distributor channel manager.  |  Organizations can onboard B2B sellers as prospects using the new B2B seller prospect type. Businesses with an indirect selling model, who sell through a network of resellers such as distributors, wholesalers, or dealers, can onboard their organizations in the system. Upon approval of the B2B seller prospect, the system creates a B2B online channel associated with the B2B seller. Specifics such as catalogs, inventory, pricing, and promotions can then be controlled at a channel level. Following the successful onboarding, an employee record is created, granting admin members from the B2B seller organization access to manage orders and stock using headless commerce APIs. A customer hierarchy is also generated, designed to streamline user management for the B2B seller organization.  | Feature management<p><p>"Enable B2B2B setup and enhancements to B2B Commerce orders"  |
| Copilot | [Generate product enrichment content for e-commerce sites with Copilot in site builder](/dynamics365/release-plan/2023wave2/commerce/dynamics365-commerce/generate-engaging-product-content-e-commerce-websites-using-copilot-dynamics-365-commerce).| Transform your product storytelling and marketing strategy with copilot functionality. This feature allows to you leverage AI-generated product marketing and enrichment content tailored to engage and delight your diverse customer base. | Admin must enable Copilot in site builder through feature configuration available in **Tenant settings** |
| Orders  |  Order history improvements   |  Registered users visiting an e-commerce website can now seamlessly search for their orders using order number, confirmation number, or origin channel name. To enhance search precision, users can filter orders based on criteria such as origin channel, order creation date range, and order status.  |  Site author  |
| POS | Cash management for multiple currencies in a store. | Cash management operations in the store, such as declare start amount, tender removal, and float entry now support multiple currencies, enabling retailers to manage cash across various currencies in a store. | By default |

## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.38 includes platform updates. To learn more, see [Platform updates for version 10.0.38 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-38.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.38, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=857683).

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
