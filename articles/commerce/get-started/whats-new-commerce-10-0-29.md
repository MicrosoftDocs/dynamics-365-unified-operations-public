---
title: Preview of Dynamics 365 Commerce 10.0.29 (October 2022)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.29. 
author: josaw1
ms.date: 08/01/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# Preview of Dynamics 365 Commerce 10.0.29 (October 2022)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.29. This version has a build number of XXXXX and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** October 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---------|------------------|----------------|--------------| 
|B2B| [Enable support for sales agreement across channels](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/enable-b2b-sales-agreement-contract-based-pricing) | This feature enables B2B seller organizations to use sales agreements in Commerce headquarters to define contract-based pricing for their buyers. When a B2B buyer shops on the e-commerce website, the contract-based pricing configured for the B2B buyer organization is automatically applied to the entire product discovery, purchase, and checkout experience.| Feature management<p>*Support for sales agreement across commerce channels* |  
|Customer Service|[Enable Customer Service with Dynamics 365 Omnichannel for Customer Service](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/chat-dynamics-365-commerce-omnichannel-customer-service) |A first-class customer support experience is key to providing a personalized and delightful commerce experience for consumers. Multiple commerce touchpoints exist today, such as physical stores, online channels, and social channels. Consumers expect a personalized support experience in all of them. This feature helps you increase cart conversions to sales, increase personalized engagement with consumers, and enhance customer service by integrating with Dynamics 365 Omnichannel for Customer Service.|Enabled by admin/makers |
| E-commerce   |  Support for product comparison in e-commerce  |  Enable shoppers to compare products across a wide range of categories in order to make the right purchase decision for themselves. This feature is available for both B2C and B2B sites.  |  Site builder  | 
| Gift cards | Support for retail gift card tables for cross-company data sharing  |  Dynamics headquarters supports the ability to enable cross-company data sharing for specific tables within the Dynamics architecture. With this feature, Dynamics 365 Commerce adds support for the retail gift card tables for cross-company data sharing. Now, a gift card in one company can have its data duplicated to another company within the environment. Changes made to the originating company gift card table will be shared to the duplicated company gift card table. | Developers  |
| Performance | Remove RTS dependency for "edit customer" scenarios   |  High availability and high performance are default expectations for point of sale (POS) and e-commerce channels. To help meet these expectations, Dynamics 365 Commerce channels no longer need to rely on real-time communication with Commerce headquarters when customer information is edited. The ability to edit customer information asynchronously for async and non-async customers can reduce real-time calls to Commerce headquarters.| Enabled by admin/makers  |




## Feature state changes in this release

The following table lists features that became mandatory or on by default starting in 10.0.29. All of these features will automatically be turned on for your system as soon as you update to 10.0.29. Mandatory features can't be turned off, but features that are on by default can still be turned off using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The table also lists features that were previously in public preview, but have changed to become generally available in 10.0.29, which means they are now recommended for use on production environments. These features are turned off by default unless otherwise noted, so you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them.

| Module | Feature name | New feature state |
| --- | --- | --- |




## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Commerce 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of Finance and Operations apps (June 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md). 

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.29, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=694438). 

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
