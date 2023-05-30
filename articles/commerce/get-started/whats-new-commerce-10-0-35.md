---
title: Preview of Dynamics 365 Commerce 10.0.35 (July 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.35. 
author: josaw1
ms.date: 05/26/2023
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-04-31
ms.dyn365.ops.version: 10.0.34
---

# Preview of Dynamics 365 Commerce 10.0.35 (July 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.35. This version has a build number of 10.0.1627 and is available on the following schedule:

- **Preview of release:** May 2023
- **General availability of release (self-update):** July 2023
- **General availability of release (auto-update):** August 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
|e-Commerce Framework | [Enable catalog support for "on behalf of" ordering](/dynamics365/release-plan/2023wave1/commerce/dynamics365-commerce/order-behalf-b2b-buyer) | This new functionality allows B2B account managers to sign into the B2B e-commerce website on behalf of the B2B buyers they work with. The feature now includes catalog support. The account manager can view all the same information that the buyer sees and can take actions such as adding items to the cart and placing orders. The feature is enabled by default in the Feature Management workspace.<p>[Enable on behalf of (OBO) functionality](../on-behalf-of.md) | Default |
| Orders | Cancel asynchronous customer orders | When this feature is enabled from the Feature Management workspace and the point of sale (POS) is using asynchronous customer orders, if the customer wants to cancel the order after placing it, the store associate will be able to cancel the asynchronous customer order and refund the customer deposit, if any.<p>[Customer orders in point of sale (POS)](../customer-orders-overview.md#enable-customer-orders-to-be-created-in-asynchronous-mode) | IT Pro opt-in |



## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Commerce version 10.0.35 includes platform updates. To learn more, see [Platform updates for version 10.0.35 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-35.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.35, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=X).

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
